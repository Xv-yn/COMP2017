# Lecture 3 Structures and Unions

Structures have an array-like organization.
- Laid out in memory in a contiguous manner (laid out continuously)
- Has a starting address
- Size depends on the number of elements and their types

A visual representation of its storage in memory:

```
+-----+----------+------------+-------------+------+
| ... |    ...   |     ...    |     ...     |  ... |
+-----+----------+------------+-------------+------+
<-------------------size of struct---------------->
```

In a way, it could be said that structures are very similar to classes in java.


#### Prerequisite Knowledge

###### Enumerator
Enumerator is a 'function' (professionally called a construct), `enum`, that assigns an integer value to symbolic names. This allows for more readable code.
```
enum color {
    red, purple, pink, green, blue = 512, black = -20
};
```
When using `enum`, C automatically assigns the first symbolic name to 0 unless otherwise defined.

In the above example:
```
red = 0
purple = 1
pink = 2
green = 3
blue = 512
black = -20
```

#### Example of a Structure
In the below example, it is assumed that there already exists code for the enumeration of `day_num` and `month_name`.
```
struct date {
    enum day_name   day;
    int             day_num;
    enum month_name month;
    int             year;
}

struct date deadline = {Monday, 1, January, 2009};
struct date *current = &deadline;

deadline.day;
(*current).day;
current -> day;

deadline.day_num;
deadline.month;
deadline.year;
```

#### Padding

Padding is a method used by the compiler to organize the memory such that certain types of data (such as integers or floating-point numbers) are aligned at memory addresses that are multiples of their size (due to computer architecture). For example, a 4-byte integer may need to be stored at an address that is divisible by 4.

Thus, proper alignment can improve memory access performance because it allows the CPU to read or write data more efficiently.

For example in the following organiation of a structure, there is a padding used to ensure that the integer is aligned at memory addresses that is a multiple of 4 (assuming ints are 4 bytes).
```
struct Example {
    char a;
    int b;
    int c;
    char d;
};

+------+----------+------------+-------------+-------+
| char |    pad   |     int    |     int     |  char |
+------+----------+------------+-------------+-------+
<---------------------size of struct----------------->
```

This can be better aligned as follows:
```
struct Example {
    char a;
    char d;
    int b;
    int c;
};

+------+----------+------------+-------------+
| char |    char  |     int    |     int     |
+------+----------+------------+-------------+
<------------------size of struct------------>
```

#### Unions


A union is similar to a structure. The only difference is that instead of 'linking' each type of data by memory, it allows for the the different data types to be stored in the same emory location.

```
union Example{
    char a;
    int b;
};

// How a Union of the above is stored in Memory
+----------+
|    int   |
+----------+
<Union Size>
```
Hence, the maximum size of a union is the maximum size of the data type stored in the union.
