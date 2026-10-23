# Changelog

Format: version, date, what changed. Newest on top.
Rule: fixing a bug = 1.0.1, 1.0.2 ... / adding a feature = 1.1.0, 1.2.0 ... / big change = 2.0.0.

## 1.2.0 - 2026-10-22
- The Queue is now really used. Each product keeps its batches in a queue (earliest expiry at the head) and stock out takes from the head (FEFO). The Reports page has a new "Sell first (FEFO queue)" table that is built from `fefoQueue()`.
- Added a unit test for the FEFO queue (15 tests in total)
- Updated `docs/COMPLEXITY.md` for the batch queue

## 1.1.2 - 2026-10-22
- Removed `docs/TEST_CASES.md` from the zip. The test cases now live only in the separate "StockTrack Test Cases" document. No code changes.

## 1.1.1 - 2026-10-22
- Fixed the build error "Source option 5 is no longer supported" in NetBeans (Clean and Build). The old Maven compiler plugin that NetBeans uses ignored the Java 17 setting, so `pom.xml` now sets the compiler plugin version and Java 17 directly.

## 1.1.0 - 2026-10-21
- Added MariaDB support. Use it by copying `stocktrack.properties.example` to `stocktrack.properties` (see `docs/DATABASE_SETUP.md`). Without that file the app still uses SQLite.
- Login screen now shows which database is in use
- If the database cannot be reached, the app shows an error message and closes instead of failing quietly
- Empty database no longer reloads the demo data after you delete every product
- Renamed some table columns (`qty_change`, `moved_at`, `order_date`) because `change` is a reserved word in MariaDB. **If you used v1.0.0, delete the old `stocktrack.db` before running v1.1.0.**
- Added test cases TC-32 and TC-33 for MariaDB (in the test cases document)

## 1.0.0 - 2026-10-21 (first versioned release)
- Login with Owner and Staff roles
- Side menu: Inventory, Reorder, Suppliers, Orders, Reports, History
- Inventory: search, stock in with expiry, stock out (earliest expiry first), undo, add, edit, delete, discard expired stock
- Reorder suggestions (Reorder Point and EOQ) with cheapest supplier
- Suppliers and price comparison, purchase orders (pending, approved, received, cancelled)
- Reports: best sellers, slow movers, ABC summary, find by exact name (binary search)
- History of all stock movements
- SQLite database (`stocktrack.db`) saved automatically
- Docs: complexity table, performance test, interview template, test cases (later moved out of the zip in 1.1.2)
- Benchmark.java for scalability tests

## Before 1.0.0 (internal builds, not versioned)
- Build 1: console starter with the core data structures and algorithms
- Build 2: first Swing dashboard
- Build 3: login and new design
- Build 4: reorder, suppliers, orders, reports, history, batches and expiry (FEFO)
- Build 5: side menu
- Build 6: edit product, discard expired, cancel order, benchmark
- Build 7: SQLite database instead of a text file
