// Будівельник може створювати різні продукти, використовуючи
// один і той самий процес будівництва.
class Car is
    // Автомобілі можуть відрізнятися комплектацією: типом
    // двигуна, кількістю сидінь, можуть мати або не мати GPS і
    // систему навігації тощо. Крім того, автомобілі можуть бути
    // міськими, спортивними або позашляховиками.

class Manual is
    // Посібник користувача для даної конфігурації автомобіля.


// Інтерфейс будівельників оголошує всі можливі етапи та кроки
// конфігурації продукту.
interface Builder is
    method reset()
    method setSeats(...)
    method setEngine(...)
    method setTripComputer(...)
    method setGPS(...)

// Усі конкретні будівельники реалізують загальний інтерфейс по-
// своєму.
class CarBuilder implements Builder is
    private field car:Car
    method reset()
        // Помістити новий об'єкт Car в полі "car".
    method setSeats(...) is
        // Встановити вказану кількість сидінь.
    method setEngine(...) is
        // Встановити наданий двигун.
    method setTripComputer(...) is
        // Встановити надану систему навігації.
    method setGPS(...) is
        // Встановити або зняти GPS.
    method getResult(): Car is
        // Повернути поточний об'єкт автомобіля.

// На відміну від інших породжувальних патернів, де продукти
// мають бути частиною одніє ієрархії класів або слідувати
// загальному інтерфейсу, будівельники можуть створювати
// абсолютно різні продукти, які не мають спільного предка.
class CarManualBuilder implements Builder is
    private field manual:Manual
    method reset()
        // Помістити новий об'єкт Manual у полі "manual".
    method setSeats(...) is
        // Описати кількість місць в автівці.
    method setEngine(...) is
        // Додати до посібника опис двигуна.
    method setTripComputer(...) is
        // Додати до посібника опис системи навігації.
    method setGPS(...) is
        // Додати до посібника інструкцію для GPS.
    method getResult(): Manual is
        // Повернути поточний об'єкт посібника.


// Директор знає, в якій послідовності потрібно змушувати
// працювати будівельника, щоб отримати ту чи іншу версію
// продукту. Зауважте, що директор працює з будівельником через
// загальний інтерфейс, завдяки чому він не знає тип продукту,
// який виготовляє будівельник.
class Director is
    method constructSportsCar(builder: Builder) is
        builder.reset()
        builder.setSeats(2)
        builder.setEngine(new SportEngine())
        builder.setTripComputer(true)
        builder.setGPS(true)


// Директор отримує об'єкт конкретного будівельника від клієнта
// (програми). Програма сама знає, якого будівельника
// використати, аби отримати потрібний продукт.
class Application is
    method makeCar() is
        director = new Director()

        CarBuilder builder = new CarBuilder()
        director.constructSportsCar(builder)
        Car car = builder.getResult()

        CarManualBuilder builder = new CarManualBuilder()
        director.constructSportsCar(builder)

        // Готовий продукт повертає будівельник, оскільки
        // директор частіше за все не знає і не залежить від
        // конкретних класів будівельників та продуктів.
        Manual manual = builder.getResult()
