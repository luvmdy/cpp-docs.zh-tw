---
title: 編譯器錯誤 C3856
ms.date: 11/04/2016
f1_keywords:
- C3856
helpviewer_keywords:
- C3856
ms.assetid: 242d9322-c325-4f20-be58-b2be6da56d60
ms.openlocfilehash: 1895f7db545813bd2fef209739b5f7ad144dbadc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461031"
---
# <a name="compiler-error-c3856"></a>編譯器錯誤 C3856

'type': 類別不是類別類型

此錯誤最常見的原因是泛型或樣板參數清單在定義比沒有在宣告時。

下列範例會產生 C3856:

```
// C3856.cpp
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>   // C3856
template <class T1>
template <class T2>  // extra template parameter list in definition
struct S<T>::S1{};
```

可能的解決方式：

```
// C3856b.cpp
// compile with: /c
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1{};
```

使用泛型時，也會發生 C3856:

```
// C3856c.cpp
// compile with: /clr
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GS<T>::GS2 {};   // C3856
```

可能的解決方式：

```
// C3856d.cpp
// compile with: /clr /c
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
ref struct GS<T>::GS2 {};
```