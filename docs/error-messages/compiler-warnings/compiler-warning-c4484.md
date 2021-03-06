---
title: 編譯器警告 C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: 71a3d903ba32fecac4b2d8bfc3e0a93f19d0f4ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473163"
---
# <a name="compiler-warning-c4484"></a>編譯器警告 C4484

'override_function': 符合基底 ref 類別方法 'base_class_function'，但未標示 'virtual'、 'new' override';'new' （和非 'virtual'） 會假設

進行編譯時 **/clr**，編譯器不會隱含地覆寫基底類別函式，這表示函式會取得 vtable 中的新位置。 若要解決，請明確指定函式是否覆寫。

如需詳細資訊，請參閱:

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../windows/override-cpp-component-extensions.md)

- [new （新位置 vtable 中）](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 一律發出為錯誤。 使用[警告](../../preprocessor/warning.md)隱藏 C4484 pragma。

## <a name="example"></a>範例

下列範例會產生 C4484。

```
// C4484.cpp
// compile with: /clr
ref struct A {
   virtual void Test() {}
};

ref struct B : A {
   void Test() {}   // C4484
};

// OK
ref struct C {
   virtual void Test() {}
   virtual void Test2() {}
};

ref struct D : C {
   virtual void Test() new {}
   virtual void Test2() override {}
};
```