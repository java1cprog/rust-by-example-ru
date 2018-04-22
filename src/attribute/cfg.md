# `cfg`

Условная компиляция возможна благодаря двум операторам:

* Атрибуту `cfg`: `#[cfg(...)]`, который указывается на месте атрибута
* Макросу `cfg!`: `cfg!(...)`, который можно использовать в условных выражениях

Обе инициализации имеют идентичный синтаксис для принятия аргументов.

```rust,editable
// Эта функция будет скомпилирована только в том случае, если целевая OS будет linux
#[cfg(target_os = "linux")]
fn are_you_on_linux() {
    println!("You are running linux!");
}

// А эта функция будет скомпилирована только в том случае *не* linux
#[cfg(not(target_os = "linux"))]
fn are_you_on_linux() {
    println!("You are *not* running linux!");
}

fn main() {
    are_you_on_linux();
    
    println!("Are you sure?");
    if cfg!(target_os = "linux") {
        println!("Yes. It's definitely linux!");
    } else {
        println!("Yes. It's definitely *not* linux!");
    }
}
```

### Смотрите также:

[the reference][ref], [`cfg!`][cfg], и [macros][macros].

[cfg]: https://doc.rust-lang.org/std/macro.cfg!.html
[macros]: macros.html
[ref]: https://doc.rust-lang.org/reference/attributes.html#conditional-compilation
