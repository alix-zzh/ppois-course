"50 классов, 150 полей, 100 уникальных поведений (перевод денег с одной карты на другую, проверка верного пароля и тд), 
код должен включать 30 примеров ассоциаций классов (включения одного класса в другой в качестве поле или параметров метода)
код должен включать 12 персональных исключений"
Репозиторий должен содержать readme файл с описанием всех классов, их полей методов, ассоциаций, исключений

Пример содержания readme.txt файл с описанием всех классов, их полей методов, ассоциаций, исключений
Accountant 4 5 → Payment, Salary, Invoice, Order, Driver
Address 6 5 → GPSPosition
BankAccount 4 6 →
Cargo 6 3 →
Client 3 6 →
CompanyFinance 3 12 → ExpenseTracker, ProfitAnalyzer, TaxCalculator
CustomerService 6 7 → Employee, Client, Order
Dispatcher 4 5 → Order, Driver, Vehicle
Driver 6 7 → DrivingLicense, Vehicle
DrivingLicense 4 3 →
Employee 8 4 →
Exceptions 1 11 → TransportException, ClientException, OrderException, etc.
ExpressDelivery 12 11 → Order, Client, Cargo
FragileCargo 8 8 → Cargo
GPSPosition 4 4 →
HRManager 4 6 → Employee
Insurance 7 4 → Vehicle
Invoice 7 4 → Client, Order
LogisticsManager 5 6 → Employee, Route, Order, Warehouse
Machine 5 5 → Vehicle
MaintenanceRecord 7 3 → Vehicle, Mechanic
Manager 5 6 → Driver, Vehicle, Order
Mechanic 4 4 → Vehicle, MaintenanceRecord
Metrics 10 9 → PerformanceMetric, FuelConsumption, TrafficInfo
Order 11 7 → Client, Cargo, Driver, Vehicle
Payment 7 4 → Client, Order
PerishableCargo 9 8 → Cargo
Route 5 5 → Address, GPSPosition
Salary 8 4 → Driver
ServiceManagement 7 10 → CustomerFeedback, ServiceQualityMonitor, LoyaltyProgram
StorageUnit 8 7 → StorageZone, Rack
TrackingSystem 2 5 → Vehicle, GPSPosition
Trailer 9 6 → Truck
TransportCompany 6 7 → Client, Driver, Vehicle, Order
Truck 3 4 → Vehicle
Van 4 4 → Vehicle
Vehicle 8 6 → Driver, GPSPosition
Warehouse 7 5 → Address, Cargo
WarehouseManager 6 6 → Employee, Warehouse, Cargo, StorageUnit
ExpenseTracker 2 4 →
ProfitAnalyzer 4 7 →
TaxCalculator 2 4 →
PerformanceMetric 4 3 →
FuelConsumption 4 3 →
TrafficInfo 3 3 →
CustomerFeedback 2 4 →
ServiceQualityMonitor 3 4 →
LoyaltyProgram 2 2 →
StorageZone 5 2 →
Rack 4 1 →

Exceptions (12):
TransportException 1 1 →
InsufficientFundsException 0 0 →
InvalidClientDataException 0 0 →
OrderNotFoundException 0 0 →
InvalidOrderDataException 0 0 →
InvalidCargoDataException 0 0 →
CargoOverweightException 0 0 →
VehicleOverloadException 0 0 →
VehicleNotAvailableException 0 0 →
DriverNotAvailableException 0 0 →
InvalidLicenseException 0 0 →

Поля: 193

Поведения : 175

Ассоциации: 67

Исключения: 12