# Lab Assignment #3. Large-Scale OOP Project

## Assignment

The requirements are fully identical to Lab Assignment #2 (see `lab2.md`),
but must be completed for a **new subject domain**, assigned individually —
different from the one used in Lab Assignment #2.

The subject domain is assigned individually per variant. For your domain,
design and implement an object model that satisfies the following
quantitative requirements:

- at least **50 classes**;
- at least **150 fields** (across all classes combined);
- at least **100 unique behaviors** — substantive methods implementing
  domain logic (for example: transferring money from one card to another,
  validating a password, etc.), not getters/setters;
- at least **30 associations** between classes — cases where one class is
  included in another as a field or a method parameter;
- at least **12 custom exception classes**.

The repository must contain a `README` file describing all classes, their
fields, methods, associations, and exceptions.

## Example README Layout

The example below (the "Transport Company" domain) illustrates the
description format and the expected level of detail. The actual domain is
assigned individually and may be entirely different from the example — this
section is a formatting sample, not mandatory content.

Row format: `Class | number of fields | number of methods | related classes`.

| Class | Fields | Methods | Associations (related classes) |
|---|---|---|---|
| Accountant | 4 | 5 | Payment, Salary, Invoice, Order, Driver |
| Address | 6 | 5 | GPSPosition |
| BankAccount | 4 | 6 | — |
| Cargo | 6 | 3 | — |
| Client | 3 | 6 | — |
| CompanyFinance | 3 | 12 | ExpenseTracker, ProfitAnalyzer, TaxCalculator |
| CustomerService | 6 | 7 | Employee, Client, Order |
| Dispatcher | 4 | 5 | Order, Driver, Vehicle |
| Driver | 6 | 7 | DrivingLicense, Vehicle |
| DrivingLicense | 4 | 3 | — |
| Employee | 8 | 4 | — |
| Exceptions | 1 | 11 | TransportException, ClientException, OrderException, etc. |
| ExpressDelivery | 12 | 11 | Order, Client, Cargo |
| FragileCargo | 8 | 8 | Cargo |
| GPSPosition | 4 | 4 | — |
| HRManager | 4 | 6 | Employee |
| Insurance | 7 | 4 | Vehicle |
| Invoice | 7 | 4 | Client, Order |
| LogisticsManager | 5 | 6 | Employee, Route, Order, Warehouse |
| Machine | 5 | 5 | Vehicle |
| MaintenanceRecord | 7 | 3 | Vehicle, Mechanic |
| Manager | 5 | 6 | Driver, Vehicle, Order |
| Mechanic | 4 | 4 | Vehicle, MaintenanceRecord |
| Metrics | 10 | 9 | PerformanceMetric, FuelConsumption, TrafficInfo |
| Order | 11 | 7 | Client, Cargo, Driver, Vehicle |
| Payment | 7 | 4 | Client, Order |
| PerishableCargo | 9 | 8 | Cargo |
| Route | 5 | 5 | Address, GPSPosition |
| Salary | 8 | 4 | Driver |
| ServiceManagement | 7 | 10 | CustomerFeedback, ServiceQualityMonitor, LoyaltyProgram |
| StorageUnit | 8 | 7 | StorageZone, Rack |
| TrackingSystem | 2 | 5 | Vehicle, GPSPosition |
| Trailer | 9 | 6 | Truck |
| TransportCompany | 6 | 7 | Client, Driver, Vehicle, Order |
| Truck | 3 | 4 | Vehicle |
| Van | 4 | 4 | Vehicle |
| Vehicle | 8 | 6 | Driver, GPSPosition |
| Warehouse | 7 | 5 | Address, Cargo |
| WarehouseManager | 6 | 6 | Employee, Warehouse, Cargo, StorageUnit |
| ExpenseTracker | 2 | 4 | — |
| ProfitAnalyzer | 4 | 7 | — |
| TaxCalculator | 2 | 4 | — |
| PerformanceMetric | 4 | 3 | — |
| FuelConsumption | 4 | 3 | — |
| TrafficInfo | 3 | 3 | — |
| CustomerFeedback | 2 | 4 | — |
| ServiceQualityMonitor | 3 | 4 | — |
| LoyaltyProgram | 2 | 2 | — |
| StorageZone | 5 | 2 | — |
| Rack | 4 | 1 | — |

### Exceptions (12)

- TransportException
- InsufficientFundsException
- InvalidClientDataException
- OrderNotFoundException
- InvalidOrderDataException
- InvalidCargoDataException
- CargoOverweightException
- VehicleOverloadException
- VehicleNotAvailableException
- DriverNotAvailableException
- InvalidLicenseException

### Example Summary Statistics

| Metric | Value |
|---|---|
| Fields | 193 |
| Behaviors | 175 |
| Associations | 67 |
| Exceptions | 12 |
