### Строгий режим — "use strict"

JavaScript развивался без проблем с обратной совместимостью, но это сохраняло ошибки в языке. В 2009 году с появлением ECMAScript 5 (ES5) добавили возможность включать строгий режим через директиву `"use strict"`, которая активирует современный режим работы кода.

#### Особенности:
- **Расположение**: Директива должна находиться в первой строке скрипта, иначе строгий режим не включится.
- **Невозможность отмены**: Нет обратной директивы для отмены строгого режима.
- **Консоль браузера**: В консоли по умолчанию строгий режим выключен, но его можно включить вручную.
- **Использование в функциях**: Можно применять строгость локально в функциях.
- **Автоматическое включение**: В современных классах и модулях строгий режим включается автоматически.