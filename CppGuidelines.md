# SE117 C++ Guidelines

## Write in ISO Standard C++

* Avoid dependence on undefined behavior (e.g. undefined order of evaluation)
* Be aware of constructs with implementation defined meaning (e.g. `sizeof(int)`)
* Do not use any extensions provided by specific compilers (e.g. g++, microsoft's cl.exe)

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

## Reference

This guideline is based on [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) and [style document of Programming: Principles and Practice using C++](http://www.stroustrup.com/Programming/PPP-style.pdf).
