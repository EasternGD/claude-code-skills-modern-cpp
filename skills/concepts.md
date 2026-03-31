---
name: concepts
description: C++20 Concepts — defining, using, and composing constraints
---

## Defining a Concept

```cpp
#include <concepts>

template<typename T>
concept Numeric = std::integral<T> || std::floating_point<T>;

template<typename T>
concept Printable = requires(T t) {
    { std::cout << t } -> std::same_as<std::ostream&>;
};

template<typename T>
concept Container = requires(T c) {
    { c.begin() } -> std::input_or_output_iterator;
    { c.end()   } -> std::input_or_output_iterator;
    { c.size()  } -> std::convertible_to<std::size_t>;
};
```

## Using Concepts

```cpp
// requires clause
template<typename T> requires Numeric<T>
T square(T x) { return x * x; }

// abbreviated function template
auto square(Numeric auto x) { return x * x; }

// constrained auto
void print(Printable auto const& val) {
    std::cout << val << '\n';
}
```

## Composing Concepts

```cpp
template<typename T>
concept SortableContainer = Container<T> && requires(T c) {
    std::sortable<decltype(c.begin())>;
};
```

## Common Standard Concepts

| Concept | Header | Meaning |
|---------|--------|---------|
| `std::integral<T>` | `<concepts>` | integer type |
| `std::floating_point<T>` | `<concepts>` | float/double |
| `std::same_as<T,U>` | `<concepts>` | exact same type |
| `std::derived_from<T,B>` | `<concepts>` | T inherits B |
| `std::invocable<F,Args...>` | `<concepts>` | callable |
| `std::ranges::range<T>` | `<ranges>` | range type |
