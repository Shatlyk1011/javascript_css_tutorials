## Виртуальный дом 

React Virtual DOM — это представление DOM в памяти. DOM - это объектная модель документа, которая представляет содержимое документов `XML` или `HTML` в виде древовидной структуры. DOM представляет весь пользовательский интерфейс вашего приложения
  * ### Недостатки настоящего DOM
  Каждый раз, когда DOM обновляется, обновленный элемент и его дочерние элементы должны быть отрисованы снова, чтобы обновить UI нашей страницы.

  * ### Что такое виртуальный DOM?
  VirtualDOM в React — это облегченная копия реального DOM ( виртуальное представление DOM), используемая для оптимизации обновлений на веб-странице. 

## Как работает Virtual DOM?
  1. При каждом изменении стейтов или пропсов, весь пользовательский интерфейс перерисовывается в представлении Virtual DOM.
  
  2. Затем вычисляется разница между предыдущим представлением DOM и новым.
  
  3. После завершения расчетов реальный DOM будет обновлен только теми вещами, которые действительно изменились.
