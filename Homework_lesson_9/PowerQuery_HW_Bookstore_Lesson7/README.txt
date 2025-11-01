Power Query Homework – Bookstore Dataset

Files:
- Books.csv        (BookID, Title, Author, Genre, Publisher, ListPrice) – has duplicate row, casing issue in Publisher, and extra spaces in Title
- Customers.csv    (CustomerID, CustomerName, City, Email) – trailing spaces, null email, duplicate row, city short forms (Calg., Tor., Van., Mtl.)
- Orders_Files/    (Monthly Orders: Orders_2022_09..12, ~120 rows each + duplicate + error row)
    Columns: OrderID, OrderDate*, CustomerID, BookID, Quantity*, Discount*, UnitPrice*, PaymentMethod*
    *messy on purpose: mixed date formats; Quantity with large values; Discount as number/%/blank; UnitPrice with $/comma/plain; PaymentMethod casing
- Publishers.csv   (Publisher, Country, ContactEmail) – for joins via Books.Publisher
- Returns.csv      (OrderID, ReturnReason) – to anti-join/filter returned orders

Suggested Homework (Power Query):
1) From Folder: append all Orders_*.csv → one table; remove duplicates & errors.
2) Convert OrderDate to a real Date; normalize PaymentMethod to proper case.
3) Clean Discount: '10%'→0.10; blanks→0. Clean UnitPrice: strip '$' and commas → Decimal.
4) Compute Revenue = Quantity * UnitPrice * (1-Discount). Add Month from OrderDate.
5) Merge with Books (BookID), then with Publishers (by Publisher), then with Customers (CustomerID).
6) Clean text: trim CustomerName; fix Title spacing; standardize City ('Calg.'→'Calgary', etc.).
7) Join with Returns to flag returned orders; optionally filter them out.
8) Load to Excel; create PivotTables (Revenue by Genre, by City, Top 10 Titles) + one PivotChart.
