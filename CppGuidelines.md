# SE117 C++ Guidelines

Chapters marked as advanced are for those who have some experience with C/C++.
Don't panic if you do not understand them.

## Write in ISO Standard C++

* Avoid dependence on undefined behavior (e.g. undefined order of evaluation)
* Be aware of constructs with implementation defined meaning (e.g. `sizeof(int)`)
* Do not use any extensions provided by specific compilers (e.g. g++, microsoft's cl.exe)
* Throw away ancient tools such as VC6 and Borland Turbo C++. They are so old
  that they cannot speak even ISO C++98

## Don't place two statement on the same line

```c++
int x = 7; char* p = 29;    // don't
int x = 7; f(x);  ++x;      // don't
```

## State intent in comments

Code says what is done, not what is supposed to be done.
Often intent can be stated more clearly and concisely than
the implementation.

```c++
void stable_sort(Sortable& c)
    // sort c in the order determined by <, keep equal elements (as defined by ==) in
    // their original relative order
{
    // ... quite a few lines of non-trivial code ...
}
```

## Don't say in comments what can be clearly stated in code

```c++
auto x = m * v1 + vv;   // multiply m with v1 and add the result to vv
```

## Use a consistent naming style

Use a single capital letter to start a type name, e.g. `Table` and `Temperature`.
Names of non-types are not capitalized, e.g. `x` and `var`.

We use underscores for multi-part names, e.g. `initial_value` and `symbol_tbl`.
Use meaningful names. Don’t overuse acronyms. Don’t use excessively
long names, such as `remaining_free_slots_in_symbol_table`.

The length of a name should be roughly proportional to the size of its scope.

Be careful when using letters and digits that are easily misread: `0Oo1lL`.

Use `ALL_CAPS` for macro names only.

## Use `Stroustrup` layout

4 space indentation

```c++
struct Cable {
    int x;
    // ...
};

double foo(int x)
{
    if (0 < x) {
        // ...
    }
    else {
        // ...
    }

    switch (x) {
        case 0:
            // ...
            break;
        case amazing:
            // ...
            break;
        default:
            // ...
            break;
    }

    if (0 < x)
        ++x;

    if (x < 0)
        something();
    else
        something_else();

    return some_value;
}
```

## Pay attentation to warnings

A program should compile cleanly; that is, it should compile without errors (or it won’t run) and warnings
(most warnings point to a potential problem).

## Avoid legacy practices (advanced)

Although C++ was formerly named "C with Classes", this is not the case
nowadays. A common practice in C or ancient C++ may be considered harmful in
modern C++.

### Use C++ equivalences to C library functions

* Use `std::cout`, `std::fstream` instead of `printf` and `FILE *`.
* Use `std::string` instead of `char[]` and `strxxx()`.
* Use smart pointers for individual objects, and STL (Standard Template
  Library) containers for multiple objects instead of (error-prone) dynamic
  memory management with `malloc()` and `free()`. Even if you want manual heap
  allocation (not recommended), use `new`, `new []` and `delete`, `delete []`
  instead.
* Use `std::sort`, `std::binary_search` instead of slow and hard-to-use
  `qsort()` and `bsearch()`.
* Use RNGs (Randon Number Generators) in `<random>` header instead of `rand()` in
  `<cstdlib>`.

And much more.

### Use Pointers at your own risk

Pointers can easily go wrong. Besides smart pointers and STL containers
mentioned above, references can also replace some pointer uses, especially in
function parameters.

There are exceptions though, but only use pointers if you know the risk.

### Get familiar with STL

There is no linked list, hash table or fancy algorithm provided by the C
library, but they are all there in C++ STL. If you want some data structure or
algorithm, check for STL first before you write your own version.

In one word, do not reinvent the wheels.

## Reference

This guideline is based on [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) and [style document of Programming: Principles and Practice using C++](http://www.stroustrup.com/Programming/PPP-style.pdf).
