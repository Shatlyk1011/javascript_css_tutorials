Давайте разберем принципы SOLID, используя доступный язык и примеры на JavaScript. Эти принципы — ключевые в объектно-ориентированном программировании и помогают создавать масштабируемые и поддерживаемые системы.

S: Single Responsibility Principle (Принцип единственной ответственности)
Описание: Каждый модуль или класс должен иметь только одну причину для изменения. Это означает, что в классе должна быть только одна задача.

Пример:

Плохо:

javascript
Copy code
class UserSettings {
  constructor(user) {
    this.user = user;
  }

  changeEmail(newEmail) {
    // Проверка email
    this.user.email = newEmail;
    // Отправка email пользователю
  }
}
Хорошо:

javascript
Copy code
class User {
  constructor(user) {
    this.user = user;
  }

  setEmail(newEmail) {
    this.user.email = newEmail;
  }
}

class EmailSender {
  sendEmail(userEmail) {
    // Отправка email
  }
}
O: Open/Closed Principle (Принцип открытости/закрытости)
Описание: Системы должны быть открыты для расширения, но закрыты для модификации. Это значит, что вы должны иметь возможность добавлять новую функциональность без изменения существующего кода.

Пример:

Плохо:

javascript
Copy code
function drawShape(shape) {
  if (shape.type === 'circle') {
    drawCircle(shape);
  } else if (shape.type === 'square') {
    drawSquare(shape);
  }
}
Хорошо:

javascript
Copy code
class Shape {
  draw() {}
}

class Circle extends Shape {
  draw() {
    // Рисуем круг
  }
}

class Square extends Shape {
  draw() {
    // Рисуем квадрат
  }
}

function drawShape(shape) {
  shape.draw();
}
L: Liskov Substitution Principle (Принцип подстановки Лисков)
Описание: Объекты в программе должны быть заменяемы на экземпляры их подтипов без изменения правильности выполнения программы.

Пример:

Плохо:

javascript
Copy code
class Bird {
  fly() {
    // Логика полета
  }
}

class Duck extends Bird {}
class Ostrich extends Bird {} // Страус не умеет летать
Хорошо:

javascript
Copy code
class Bird {}
class FlyingBirds extends Bird {
  fly() {
    // Логика полета
  }
}

class Duck extends FlyingBirds {}
class Ostrich extends Bird {}
I: Interface Segregation Principle (Принцип разделения интерфейса)
Описание: Клиенты не должны быть вынуждены зависеть от интерфейсов, которые они не используют.

Пример:

Плохо:

javascript
Copy code
class Worker {
  work() {}
  eat() {}
}

class Robot extends Worker {
  eat() {
    // Не нужно для робота
  }
}
Хорошо:

javascript
Copy code
class Worker {
  work() {}
}

class Eater {
  eat() {}
}

class HumanWorker extends Worker, Eater {
  work() {}
  eat() {}
}

class RobotWorker extends Worker {
  work() {}
}
D: Dependency Inversion Principle (Принцип инверсии зависимостей)
Описание: Модули высокого уровня не должны зависеть от модулей низкого уровня. Оба типа модулей должны зависеть от абстракций.

Пример:

Плохо:

javascript
Copy code
class LightBulb {
  turnOn() {}
  turnOff() {}
}

class ElectricPowerSwitch {
  constructor(bulb) {
    this.bulb = bulb;
  }

  press() {
    if (this.bulb.isOn) {
      this.bulb.turnOff();
    } else {
     