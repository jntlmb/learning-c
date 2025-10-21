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

### Structures
- Coming soon...

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
