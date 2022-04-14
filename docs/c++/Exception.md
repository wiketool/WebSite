---
id: Exception
title: C++常见异常
description: 常用异常
---

### std::invalid_argument

```cpp
throw std::invalid_argument(" idx invalid argument");
```

```cpp
try {
    std::bitset<4>{"012"}; // Throws: only '0' or '1' expected
} catch (std::invalid_argument const& ex) {
    std::cout << "#1: " << ex.what() << '\n';
}
```

