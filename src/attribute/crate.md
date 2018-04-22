# Контейнеры

Атрибут `crate_type` используется, чтобы сказать компилятору,
какой контейнер является библиотекой (и каким типом библиотеки),
а какой исполняемым файлом. Атрибут `crate_name` используется для указания имя контейнера.

However, it is important to note that both the `crate_type` and `crate_name`
attributes have **no** effect whatsoever when using Cargo, the Rust package
manager. Since Cargo is used for the majority of Rust projects, this means
real-world uses of `crate_type` and `crate_name` are relatively limited.

```rust,editable
// Этот контейнер - библиотека
#![crate_type = "lib"]
// Эта библиотека называется "rary"
#![crate_name = "rary"]

pub fn public_function() {
    println!("вызвана rary's `public_function()`");
}

fn private_function() {
    println!("вызвана rary's `private_function()`");
}

pub fn indirect_access() {
    print!("вызвана rary's `indirect_access()`, которая\n> ");

    private_function();
}
```

Если мы используем атрибут `crate_type`,
то нам больше нет необходимости передавать флаг `--crate-type` компилятору.

```bash
$ rustc lib.rs
$ ls lib*
library.rlib
```
