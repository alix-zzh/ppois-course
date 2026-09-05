# Лабораторная работа №3. Крупный ООП-проект

## Задание

Требования полностью аналогичны лабораторной работе №2 (см. `lab2.md`), но
выполняются на **новой предметной области**, назначенной индивидуально —
отличной от той, что использовалась в лабораторной работе №2.

Предметная область (домен) назначается индивидуально по варианту. Для
своего домена нужно спроектировать и реализовать объектную модель,
удовлетворяющую следующим количественным требованиям:

- не менее **50 классов**;
- не менее **150 полей** (суммарно по всем классам);
- не менее **100 уникальных поведений** — содержательных методов,
  реализующих логику предметной области (например: перевод денег с одной
  карты на другую, проверка корректности пароля и т. п.), а не
  геттеров/сеттеров;
- не менее **30 ассоциаций** между классами — случаев, когда один класс
  включён в другой в качестве поля или параметра метода;
- не менее **12 собственных классов исключений**.

Репозиторий должен содержать файл `README`, описывающий все классы, их
поля, методы, ассоциации и исключения.

## Пример оформления README

Пример ниже (предметная область «Транспортная компания») иллюстрирует
формат описания и ожидаемую степень детализации. Конкретный домен
назначается индивидуально и может полностью отличаться от примера —
раздел приведён как образец оформления, а не как обязательное содержание.

Формат строки: `Класс | число полей | число методов | связанные классы`.

| Класс | Поля | Методы | Ассоциации (связанные классы) |
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
| Exceptions | 1 | 11 | TransportException, ClientException, OrderException и др. |
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

### Исключения (12)

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

### Итоговая статистика примера

| Показатель | Значение |
|---|---|
| Поля | 193 |
| Поведения | 175 |
| Ассоциации | 67 |
| Исключения | 12 |
