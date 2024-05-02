# Преобразование типов

#### В программировании преобразование типов — это процесс преобразования данных одного типа в другой. Например, преобразование строковых данных в число.

В JavaScript существует два типа преобразования типов:

* Явное преобразование — преобразование типов вручную.

* Неявное преобразование — автоматическое преобразование типов.

#### Примеры: 
 * `Строковое преобразование` происходит, когда требуется представление чего-либо в виде строки.
  ```
  value = String(value); // теперь value это строка "true"
  alert(typeof value); // string
  ```

 * `Численное преобразование` Численное преобразование происходит в математических функциях и выражениях.
  ``` 
  alert( "6" / "2" );    // 3, строки преобразуются в числа
  Number("   123   ") ; // 123
  Number("123z");        // NaN (ошибка чтения числа на месте символа "z")
  Number(true);          // 1
  Number(false) ;        // 0
  ```
  * `Логическое преобразование`
  ```
  Boolean(1);         // true
  Boolean(0);         // false
  Boolean("0");       // true
  Boolean("Привет!"); // true
  Boolean("");        // false
  ```

  //Преобразование объектов в примитивы