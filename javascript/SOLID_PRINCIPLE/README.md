Принципы SOLID - это пять основных принципов объектно-ориентированного программирования, которые помогают сделать код более устойчивым к изменениям, читаемым и легким в сопровождении. 

S: Single Responsibility Principle (Принцип единственной ответственности)
Описание: Каждый класс должен отвечать только за одну вещь. Это означает, что у класса должна быть только одна причина для изменения.

Плохо:
```javascript
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
```
Хорошо:

```javascript
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
```
<br/>
<br/>
O: Open/Closed Principle (Принцип открытости/закрытости)
Описание: Системы должны быть открыты для расширения, но закрыты для модификации. Это значит, что вы должны иметь возможность добавлять новую функциональность без изменения существующего кода.

Пример:

Плохо:

```javascript
function drawShape(shape) {
  if (shape.type === 'circle') {
    drawCircle(shape);
  } else if (shape.type === 'square') {
    drawSquare(shape);
  }
}
```
Хорошо:

```javascript
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
```
<br/>
<br/>
L: Liskov Substitution Principle (Принцип подстановки Лисков)
Описание: Объекты базового класса должны без проблем заменяться объектами подклассов.

Пример:

Плохо:

```javascript 
class Bird {
  fly() {
    // Логика полета
  }
}

class Duck extends Bird {}
class Ostrich extends Bird {} // Страус не умеет летать
```

Хорошо:
```javascript
class Bird {}
class FlyingBirds extends Bird {
  fly() {
    // Логика полета
  }
}

class Duck extends FlyingBirds {}
class Ostrich extends Bird {}
```
<br/>
<br/>
I: Interface Segregation Principle (Принцип разделения интерфейса)
Описание: Клиенты не должны зависеть от интерфейсов, которые они не используют. Это означает, что лучше иметь несколько специализированных интерфейсов, чем один универсальный.

Плохо:

```javascript
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
```
Хорошо:

```javascript
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
```
<br/>
<br/>
D: Dependency Inversion Principle (Принцип инверсии зависимостей)
Описание: Модули высокого уровня не должны зависеть от модулей низкого уровня. Оба типа модулей должны зависеть от абстракций.

Пример:

Плохо:

```javascript
class Database {
    public void save(User user) {
        // логика сохранения в базу данных
    }
}

class UserService {
    private Database database;

    public UserService() {
        this.database = new Database();
    }

    public void addUser(User user) {
        database.save(user);
    }
}
```

Хорошо:
```javascript
interface UserRepository {
  void save(User user);
}

class Database implements UserRepository {
  public void save(User user) {
    // логика сохранения в базу данных
  }
}

class UserService {
  private UserRepository userRepository;

  public UserService(UserRepository userRepository) {
    this.userRepository = userRepository;
  }

  public void addUser(User user) {
    userRepository.save(user);
  }
}
```