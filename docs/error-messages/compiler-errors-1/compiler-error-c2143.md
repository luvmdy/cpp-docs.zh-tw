---
title: 編譯器錯誤 C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: ed4bc7eea85e5263d59817082caed99bde3d75d5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520110"
---
# <a name="compiler-error-c2143"></a>編譯器錯誤 C2143

語法錯誤： 遺漏 'token1'，'token2' 之前

編譯器會預期特定的權杖 （也就是空白字元以外的語言元素），卻找到另一個權杖。

請檢查[c + + 語言參考](../../cpp/cpp-language-reference.md)來判斷程式碼語法不正確的位置。 因為遇到造成問題的那一行之後，編譯器可能會報告此錯誤，請檢查幾行程式碼錯誤之前。

在不同的情況下，C2143 就會發生。

這個錯誤可能會發生在可以限定名稱的運算子 (`::`、`->` 和 `.`) 後面必須接著關鍵字 `template`，如下列範例所示：

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

根據預設，C++ 假設 `Ty::PutFuncType` 不是範本；因此下列 `<` 會解譯成小於符號。  您必須明確地告知編譯器 `PutFuncType` 為範本，以便它可以正確地剖析角括號。 若要更正這個錯誤，請在相依類型名稱上使用 `template` 關鍵字，如下所示：

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

C2143 就會發生時 **/clr**會使用和`using`指示詞發生語法錯誤：

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

它也可能發生於您嘗試使用不也使用的 CLR 語法編譯原始程式碼檔案 **/clr**:

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

接在 `if` 陳述式後面的第一個非空白字元必須為左括號。 編譯器無法轉譯任何其他項目：

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

偵測到錯誤的那一行或之前其中一行遺漏了右大括號、括號或分號時，C2143 就會發生：

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

或是在類別宣告中有無效的標記時：

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

或當標記未附加至陳述式。 如果您必須將標籤放本身，比方說，結尾的複合陳述式，將它附加至 null 陳述式：

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

不合格的呼叫對 c + + 標準程式庫中的型別時，可能會發生錯誤：

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

或有遺漏 `typename` 關鍵字：

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

或者如果您嘗試定義明確具現化：

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

在 C 程式中，變數必須宣告的函式開頭，它們不能宣告之後執行此函式的非宣告的指示。

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
