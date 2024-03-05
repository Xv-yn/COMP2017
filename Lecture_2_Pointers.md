# Lecture 2 Pointers

#### Overview
A pointer is a term used to describe a variable containing a memory address. Note that a memory address can be considered a "hidden" data type.

To initialize a pointer, the following code is used:
```
int *ptr;
```

What this code does is create/initialize a variable (`*ptr`) that has the data type 'memory address'. This means that the data stored in that variable should be a memory address.

The `int` is written because it 'tells' the computer to read the data stored (bit pattern) in the address as an integer. Hence, if there is a character or other data type, `int` can be replaced with its corresponding data type.

The `*` is a multi-functional operator (called an overloaded operator) that has different functions depending on how it is used.
- It is most commonly known as the multiplication operator because it very commonly acts as the multiplication symbol
- It is also known as the dereferencing operator that 'dereferences' a variable to output its corresponding data

And `ptr` is just the variable name. It can be replaced with anything, such as `pointer`.

###### Example

The following code disregards the syntax of C and focuses on the explanation of the concepts of a pointer.
```
int x = 5           // This initializes an integer variable x with the value of 5

int *ptr = &x       // This initializes a pointer with the memory address of x

print(x)            // This prints the value stored in the variable x, which is 5

print(&x)           // This prints the memory address of the variable x

print(*ptr)         // This prints the data stored in the memory address of ptr, which is 5

print(ptr)          // This prints the memory address of the variable x
```

Another way to think of a pointer would be that, after initialization, `ptr` stores 'encrypted' data (the memory address). By adding `*`, we are 'decrypting' that data. Hence, 'explaining' the following outputs.

```
print(*ptr)         // This prints the data stored in the memory address of ptr, which is 5

print(ptr)          // This prints the memory address of the variable x
```

#### Null Terminator

In C, there is no `String` data type. Rather, the '`String`' data type is identified in a more basic manner as an array of characters followed by a null terminator. The null terminator is added because functions may continue reading beyond the intended string, resulting in undefined behavior.

A null terminator, written as ` \0`, is a special character used to indicate the end of a string (like a STOP codon in biology). In more simple terms, by adding the null terminator to the end of a character array, the computer can read this array and determine exactly when the array ends, thus identifying this array as a 'valid' String.

```
char myString[10] = "Hello";
```

Using the understand of memory, this array would take up 10 bytes of memory in consecutive order (because each character takes up 1 byte of memory). This can be visualized in the following format.

```
+---+---+---+---+---+---+---+---+---+---+
| H | e | l | l | o | \0|   |   |   |   |
+---+---+---+---+---+---+---+---+---+---+
 ^   ^   ^   ^   ^   ^
 |   |   |   |   |   |
 &myString[0] ... &myString[5]
```

Because '`Hello`' contains 5 characters, each character would logically take up the memory addresses `&myString[0]` to `&myString[4]`. However, for the computer to consider this array of characters as a valid `String`, there must be a null terminator to indicate the end of the string. Hence, the null terminator takes up the memory address: `myString[5]`.

When creating a "`String`" that has no room for the null terminator in the character array, it could lead to unexpected behavior and undefined results when calling it because it is not considered a "valid" String and does not have a 'defined' end (meaning that a computer could continue reading the consecutive memory addresses as it has not been 'told' to stop).
```
char myString[5] = "Hello";  // No room for the null terminator
```

#### Command Line Arguments

```
int main(int arc, char **argv) {
    return 0;
}
```

argv is an array of C strings from the command line argument (it is an array of addresses where each address refers to a C string (The data type of a C string is a character array/ char *))

```
C: \Users\myComputer> .\myProgram.c
```




