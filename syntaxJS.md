# C++ → JavaScript Cheat Sheet

## Khai báo biến

| C++ | JavaScript |
|-----|------------|
| `int x = 5;` | `let x = 5;` |
| `const int x = 5;` | `const x = 5;` |
| `double d = 3.14;` | `let d = 3.14;` |
| `string s = "hi";` | `let s = "hi";` |
| `bool b = true;` | `let b = true;` |
| `auto x = 5;` | `let x = 5;` |
| `int x;` (chưa gán) | `let x;` (→ `undefined`) |

> JS không có kiểu cố định: dùng `let` (thay đổi được), `const` (không gán lại), tránh `var`.

## Kiểu dữ liệu

| C++ | JavaScript |
|-----|------------|
| `int`, `long`, `double`, `float` | `number` (tất cả là 1 kiểu) |
| `long long`, số rất lớn | `BigInt` (`123n`) |
| `string`, `char` | `string` (không có kiểu `char` riêng) |
| `bool` | `boolean` |
| `nullptr` | `null` |
| (không có) | `undefined` |

## Hàm

```cpp
// C++
int add(int a, int b) {
    return a + b;
}
```
```js
// JS
function add(a, b) {
  return a + b;
}
// hoặc arrow function
const add = (a, b) => a + b;
```

| C++ | JavaScript |
|-----|------------|
| `void f() {}` | `function f() {}` |
| Tham số mặc định `f(int a = 1)` | `function f(a = 1) {}` |
| Overload (cùng tên, khác kiểu) | Không có — dùng `arguments`/tham số tùy chọn |
| Truyền tham chiếu `int& x` | Object/Array truyền theo tham chiếu mặc định |

## In ra / Nhập vào

| C++ | JavaScript |
|-----|------------|
| `cout << x << endl;` | `console.log(x);` |
| `cout << a << b;` | `console.log(a, b);` |
| `cin >> x;` | `prompt()` (browser) / `readline` (Node) |
| `printf("%d", x);` | `console.log(\`${x}\`);` |

## Điều kiện

```cpp
if (x > 0) { } else if (x < 0) { } else { }
```
```js
if (x > 0) { } else if (x < 0) { } else { }
```

| C++ | JavaScript |
|-----|------------|
| `==` (so sánh giá trị) | `===` (nên dùng — so sánh cả kiểu) |
| `!=` | `!==` |
| `&&`, `\|\|`, `!` | giống hệt |
| `switch/case/break` | giống hệt |
| Ternary `a ? b : c` | giống hệt |

## Vòng lặp

```cpp
for (int i = 0; i < n; i++) { }
```
```js
for (let i = 0; i < n; i++) { }
```

| C++ | JavaScript |
|-----|------------|
| `for (auto x : arr)` | `for (const x of arr)` |
| `while (cond) {}` | giống hệt |
| `do {} while (cond);` | giống hệt |
| `break` / `continue` | giống hệt |
| (lặp index/key object) | `for (const k in obj)` |

## Mảng / Vector

| C++ | JavaScript |
|-----|------------|
| `vector<int> v = {1,2,3};` | `let v = [1, 2, 3];` |
| `int arr[3] = {1,2,3};` | `let arr = [1, 2, 3];` |
| `v.push_back(4);` | `v.push(4);` |
| `v.pop_back();` | `v.pop();` |
| `v.size();` | `v.length;` |
| `v[0];` | `v[0];` |
| `v.front()` / `v.back()` | `v[0]` / `v[v.length-1]` |
| `sort(v.begin(), v.end());` | `v.sort((a,b) => a-b);` |
| `find(...)` | `v.indexOf(x)` / `v.includes(x)` |
| `for_each` / transform | `v.forEach()` / `v.map()` |

## Map / Set

| C++ | JavaScript |
|-----|------------|
| `map<string,int> m;` | `let m = new Map();` hoặc `let m = {};` |
| `m["key"] = 1;` | `m.set("key",1)` / `m["key"]=1` |
| `m["key"];` | `m.get("key")` / `m["key"]` |
| `m.count(k)` | `m.has(k)` / `k in obj` |
| `set<int> s;` | `let s = new Set();` |
| `s.insert(x);` | `s.add(x);` |

## Chuỗi (String)

| C++ | JavaScript |
|-----|------------|
| `s.length()` / `s.size()` | `s.length` |
| `s + t` (nối) | `s + t` |
| `s.substr(i, n)` | `s.substring(i, i+n)` / `s.slice(i, i+n)` |
| `s[i]` | `s[i]` / `s.charAt(i)` |
| `to_string(x)` | `String(x)` / `x.toString()` |
| `stoi(s)` | `parseInt(s)` / `Number(s)` |
| `stod(s)` | `parseFloat(s)` |

## Class / OOP

```cpp
// C++
class Dog {
  string name;
public:
  Dog(string n) : name(n) {}
  void bark() { cout << name; }
};
```
```js
// JS
class Dog {
  constructor(name) {
    this.name = name;
  }
  bark() {
    console.log(this.name);
  }
}
```

| C++ | JavaScript |
|-----|------------|
| `Dog d("Rex");` | `let d = new Dog("Rex");` |
| `this->name` | `this.name` |
| `class B : public A {}` | `class B extends A {}` |
| `A::A()` gọi base | `super()` |
| `public/private/protected` | `#private` (private), mặc định public |
| `static int x;` | `static x;` |

## Con trỏ / Tham chiếu

| C++ | JavaScript |
|-----|------------|
| `int* p = &x;` | Không có con trỏ |
| `*p`, `&x` | Object/Array tự là "tham chiếu" |
| `new` / `delete` | `new` có; bộ nhớ tự thu hồi (GC) |
| Quản lý bộ nhớ thủ công | Garbage Collection tự động |

## Khác biệt quan trọng

- **Không cần `;` bắt buộc** trong JS (nhưng nên dùng).
- **Không khai báo kiểu** — JS là dynamic typing.
- **Không có header/`#include`** — dùng `import`/`require`.
- **Bất đồng bộ**: JS có `async/await`, `Promise` (C++ chuẩn khác hẳn).
- **`==` lỏng lẻo trong JS** — luôn ưu tiên `===`.
- **Hàm là first-class** — truyền hàm như biến rất phổ biến.
- **Không có hủy đối tượng (`~Dog()`)** — GC lo việc dọn dẹp.

## Module / Import

| C++ | JavaScript |
|-----|------------|
| `#include <iostream>` | `import` / `require` |
| `#include "myfile.h"` | `import { x } from './myfile.js'` |
| `using namespace std;` | (không cần) |
| (xuất) | `export function f() {}` |
