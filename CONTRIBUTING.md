Contributing Guidelines
=======================

## Basic Guidelines

1. Indentation: **4 spaces** (do not use tabs).
2. Maximum line length: **120** characters.
3. Names of classes in **PascalCase**, methods and variables in **camelCase**.
4. Capitalize constants: MY_CONSTANT.
5. One class per file and file name same as class name.
6. Write descriptions and comments for functions/methods above the function name.
7. Leave one extra line at the bottom of each file.
8. Don't leave whitespace at the ends of lines. A good editor handles this automatically by removing whitespace when saving the file.

## Formatting Guidelines

### Braces Usage

`If`, `elsif`, `else`, `foreach`, `for`, `while`, etc. blocks ─ always in curly braces `{ }`, even in one statement.

✅ Correct:

```nasal
if (condition) {
    x = 0;
}
```

❌ Incorrect:

```nasal
if (condition) x = 0;

if (condition)
    x = 0;
```

### Space Before Parentheses

After words like `if`, `elseif`, `for`, `foreach`, `forindex`, `while`, put a space before `()`. After function names and the keyword `func`, do not put a space before `()`, e.g.: `myFunc();` or `func(param)`.

✅ Correct:

```nasal
if (condition) {
    x = 0;
}

calcFunc();

calcFunc(func(param) {
    # closure body
});
```

❌ Incorrect:

```nasal
if(condition) {
    x = 0;
}

if ( condition ) {
    x = 0;
}

if( condition ) {
    x = 0;
}

calcFunc ();

calcFunc (func (param) {
    # closure body
});

calcFunc(func () {
    # closure body
});
```

### Generally one statement in separate line.

✅ Correct:

```nasal
if (condition) {
    x = 0;
}
```

❌ Incorrect:

```nasal
if (condition) x = 0;
if (condition) { x = 0; }

if (condition) {
    x = 0; str = '';
}
```

🧩 Exceptions may be simple map/convert functions with a large number of simple conditions:

```nasal
converter: func(numer) {
    if (numer == 1) return 'g';
    if (numer == 2) return 'h';
    if (numer == 3) return 'q';
    if (numer == 4) return 'i';
    if (numer == 5) return 'z';

    return nil;
},
```

### Always insert a comma after the last item when listing vertically.

✅ Correct:

```nasal
var acType = [
    'ga',
    'airliner',
    'military',
    'ultralight',
];

var calc = func(
    name,
    factor,
    index,
    scale,
) {
    # function body...
};
```

❌ Incorrect:

```nasal
var acType = [
    'ga',
    'airliner',
    'military',
    'ultralight'    # <- missing `,`
];

var calc = func(
    name,
    factor,
    index,
    scale    # <- missing `,`
) {
    # function body...
};
```

## Comments Guidelines

### Function Comments

Insert a comment block before each function

Each function parameter describe in the following format:

```nasal
# @param type name Description.
```

The type is especially important to avoid ambiguity. If the type can be `string`, or any number, use `scalar`. If there can be multiple types, separate them with `|`, e.g., `vector|nil`. If the type can be any type, use `mixed`. If you don't know the type of a parameter, you can check it using the `typeof(variable)` method, which return string with type name.

The return value of each function describe in the following format:

```nasal
# @return type Description.
```

The type is particularly important to avoid confusion, especially since in Nasal the function returns a value even if you don't use `return`. If you intend for the function to return nothing or it's not important, write the type `void`.

✅ Example:

```nasal
#
# Function long description.
#
# @param  string|nil  key  Key name for the hash.
# @param  double  x  Multiplier value.
# @return double  The new hash value multiplied by the given value.
#
var calc = func(key, x) {
    if (key == nil) {
        return 0;
    }

    return hash[key] * x;
};
```

### Class Comments

Also, try to describe each class in the block before the class definition. What the class is for and what problem it solves, etc.

✅ Example:

```nasal
#
# A class for automatically loading Nasal files.
#
var Loader = {
    # class body...
};
```
