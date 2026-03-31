---
name: ranges
description: C++20 Ranges and views — composable, lazy transformations over sequences
---

## Basic Usage

```cpp
#include <ranges>
#include <algorithm>
#include <vector>
#include <print>

std::vector<int> v{1, 2, 3, 4, 5, 6};

// filter + transform + take
auto result = v
    | std::views::filter([](int x){ return x % 2 == 0; })
    | std::views::transform([](int x){ return x * x; })
    | std::views::take(3);

for (int x : result) std::print("{} ", x);  // 4 16 36
```

## Common Views

```cpp
std::views::iota(1, 10)          // 1 2 3 ... 9
std::views::reverse(v)           // reversed
std::views::drop(v, 2)           // skip first 2
std::views::take_while(v, pred)  // take until pred false
std::views::zip(a, b)            // C++23: pairs
std::views::enumerate(v)         // C++23: (index, value)
std::views::chunk(v, 3)          // C++23: groups of 3
```

## Collecting Results

```cpp
// C++23
auto vec = result | std::ranges::to<std::vector>();

// C++20 workaround
std::vector<int> out;
std::ranges::copy(result, std::back_inserter(out));
```

## Algorithms

```cpp
std::ranges::sort(v);
std::ranges::sort(v, std::greater{});
std::ranges::sort(v, {}, &MyStruct::key);  // project on member

auto it = std::ranges::find(v, 42);
bool any = std::ranges::any_of(v, [](int x){ return x > 10; });
```
