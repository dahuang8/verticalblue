---
layout: post
title: C++ Multimap
---

Multimap is an extension to regular map. It allows multiple values associated with the same key. The right way to access all values associated with the same key is to use `equal_range()`.

~~~cpp
unordered_multimap<int, string> map{ {0, "a"}, {0, "b"}, {1, "c"}, {1, "d"}, {1, "e"}, {2, "f"} };
auto rtn = map.find(1);
cout << "found one entry with key " << rtn->first << " holds value " << rtn->second << endl;
cout << map.count(0) << endl;
cout << map.count(1) << endl;
cout << "equal_range:" << endl;
auto rgn = map.equal_range(1);
for_each(rgn.first, rgn.second, [](auto &v){cout << "key = " << v.first << ", value = " << v.second << endl;});
map.emplace(2, "g");
~~~

Note:

1. for all map-like containers, `find()` returns iterator with underneath data assembled as **pairs**. `first` of returned pair is the key and `second` of returned pair is the value.
2. slight differently, `equal_range(key)` return a pair with `first` refers to the iterator pointing to the beginning and `second` refers to the iterator pointing to the end.
3. bracket is not implemented for `multimap`, it's a noticable difference between `map`. to add new item, use `emplace(key, value)`.
