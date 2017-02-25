Числовые литералы могут быть обозначены добавлением типа в качестве суффикса. Например, 
чтобы указать, что литерал `42` должен иметь тип `i32`, необходимо написать `42i32`.

Тип литералов без суффикса будет зависеть от того, как они используются. Если нет никаких 
ограничений, то компилятор будет использовать `i32` для целочисленных литералов, а `f64` для 
литералов с плавающей точкой.

{literals.play}

В предыдущем коде используются некоторые вещи, которые не были объяснены ранее. 
Вот краткое объяснение для нетерпеливых читателей:

* `fun(&foo)` используется для передаче аргумента в функцию *по ссылке*, вместо
  передачи по значению (`fun(foo)`). Подробнее см. [заимствование][borrow] или соответствующую 
  [главу в книгу](http://rurust.github.io/rust_book_ru/src/references-and-borrowing.html).
* `std::mem::size_of_val` является функцией, но вызывается с указанием *полного пути*. 
  Код можно разделить на логические единицы, называемые *модулями*. В данном случае, 
  функция определена в модуле `mem`, а модуль `mem` определён в *контейнере* `std`. 
  Подробнее см. [модули][mod] и [контейнеры][crate], 
  а так же соответствующую [главу в книге](http://rurust.github.io/rust_book_ru/src/crates-and-modules.html) 

[borrow]: /scope/borrow.html
[mod]: /mod.html
[crate]: /crates.html