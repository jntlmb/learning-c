# The C Programming Language

## Main Function

```c
int main() {
    return 0;
}
```

---

## Data Types

### Integers — Whole Numbers (positive or negative)

- `char` (typically ranges from -128 to 127)
- `int`
- `short`
- `long`
- `long long`

### Unsigned Integers — Whole Numbers (only positive)

- `unsigned char`
- `unsigned int`
- `unsigned short`
- `unsigned long`
- `unsigned long long`

### Floating Point Numbers — Numbers with fractions

- `float`
- `double`

---

## Boolean Type

C originally does **not** have a built-in boolean type (before `<stdbool.h>`).  
You can define your own:

```c
#define BOOL char
#define FALSE 0
#define TRUE 1
```

Alternatively, include `<stdbool.h>` and use the built-in `bool`, `true`, and `false`.

---

## Defining Variables

For most numbers, use `int` (typically a 32-bit number):

```c
int foo;
int bar = 1;
```

---

## Constants

### Using `#define`

```c
#define PI 3.14159
#define MAX_LENGTH 100
```

### Using `const`

```c
const int max_score = 100;
const double gravity = 9.81;
```

---

## Arrays

Define an array that stores 10 integers:

```c
int numbers[10];
```

---

## Multidimensional Arrays

General form:

```c
type name[size1][size2]...[sizeN];
```

Example:

```c
int foo[1][2][3];
char vowels[1][5] = {
    {'a', 'e', 'i', 'o', 'u'}
};
```

---

## Conditions

Form of an `if` statement:

```c
int target = 20;

if (target == 20) {
    printf("Target is equal to 20");
} else if (target < 20) {
    printf("Target is less than 20");
} else {
    printf("Target is greater than 20");
}
```

---

## Strings

Strings in C are actually **arrays of chars**.

```c
char *name = "John Lizzy";  // read-only
char name[] = "John Lizzy"; // can be modified
```

Equivalent explicit declaration:

```c
char name[11] = "John Lizzy";
```

---

### String Functions

#### `strlen` — Get string length

```c
char *name = "John Lizzy";
printf("%zu\n", strlen(name)); // %zu is the correct format specifier for size_t
```

#### `strncmp` — Compare strings

Compares up to `n` characters and returns 0 if equal.

```c
char *name = "John";
if (strncmp(name, "John", 4) == 0) {
    printf("Hello, John!\n");
} else {
    printf("You are not John. Go away.\n");
}
```

#### `strncat` — Append strings

Appends the first `n` characters of `src` to `dest`.

```c
char dest[20] = "Hello";
char src[20] = "World";

strncat(dest, src, 3);
printf("%s\n", dest); // "HelloWor"

strncat(dest, src, 20);
printf("%s\n", dest); // "HelloWorWorld"
```

---

## Structs

Structs (short for _structures_) are user-defined data types that group multiple variables under one name.

```c
struct Point {
    int x;
    int y;
};
```

Creating and using structs:

```c
struct Point p1;
p1.x = 10;
p1.y = 20;

printf("x: %d, y: %d\n", p1.x, p1.y);
```

You can also initialize directly:

```c
struct Point p2 = {30, 40};
```

Accessing struct members through a pointer:

```c
struct Point *ptr = &p2;
printf("%d\n", ptr->x);  // same as (*ptr).x
```

---

## Typedef

`typedef` creates **type aliases** — new names for existing types.

### Basic typedefs

```c
typedef unsigned int uint;
typedef long long ll;
```

Now you can write:

```c
uint age = 25;
ll population = 8000000000;
```

### Typedef with Structs

You can combine `typedef` and `struct`:

```c
typedef struct {
    int x;
    int y;
} Point;
```

Now you can declare without repeating `struct`:

```c
Point p = {10, 20};
```

You can also name both the struct and the typedef:

```c
typedef struct Point {
    int x;
    int y;
} Point;
```

---

## Enums

`enum` defines a type with **named integer constants**.

```c
enum Direction {
    NORTH,
    EAST,
    SOUTH,
    WEST
};
```

By default, values start at 0 (`NORTH = 0`, `EAST = 1`, …).  
You can set specific values:

```c
enum Status {
    SUCCESS = 1,
    FAILURE = -1,
    UNKNOWN = 0
};
```

Usage:

```c
enum Status s = SUCCESS;

if (s == SUCCESS) {
    printf("Operation succeeded!\n");
}
```

---

## Unions

`union` allows storing **different data types in the same memory location**.  
Only one field can be used at a time.

```c
union Data {
    int i;
    float f;
    char str[20];
};

union Data data;
data.i = 10;
printf("%d\n", data.i);
```

Useful when working with memory or binary data formats.

---

## Pointer

A pointer is just a variable that stores a memory address

---

## In depth

### Type Sizes (in memory)

The size of a type is not guaranteed to be the same on all systems.
The size of a type is dependent on the system architecture.

32-bit system → `int` = 4 bytes  
64-bit system → `int` = 8 bytes

You can check type sizes with the `sizeof` operator:

```c
printf("%zu\n", sizeof(int));
```

#### Common Sizes

| Type     | Typical Size | Description                                  |
| -------- | ------------ | -------------------------------------------- |
| `char`   | 1 byte       | Single character (can be signed or unsigned) |
| `int`    | 4 bytes      | Integer number                               |
| `float`  | 4 bytes      | Single-precision floating-point              |
| `double` | 8 bytes      | Double-precision floating-point              |

---

## Preprocessor Directives

Preprocessor directives are instructions executed **before compilation**.

- `#include` — include header files
- `#define` — define constants or macros
- `#ifdef`, `#ifndef`, `#endif` — conditional compilation

Example header guard:

```c
#ifndef POINT_H
#define POINT_H

struct Point {
    int x;
    int y;
};

#endif
```
