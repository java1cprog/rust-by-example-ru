# Замораживание

Когда данные заимствуются, они заодно и *замораживаются*. *Замороженные* данные
не могут быть изменены до тех пор, пока все ссылки не выйдут за область видимости:

```rust,editable,ignore,mdbook-runnable
#[allow(unused_assignments)]
fn main() {
    let mut mutable_integer = 7i32;

    {
        // Заимствовать `_mutable_integer`
        let _large_integer = &mutable_integer;

        // Ошибка! `_mutable_integer` заморожен в этой области видимости
        mutable_integer = 50;
        // ИСПРАВЬТЕ ^ Закомментируйте эту строку

        // `_large_integer` покидает область видимости
    }

    // Ок! `_mutable_integer` не заморожен в этой области видимости
    mutable_integer = 3;
}
```
