---
title: 編譯器錯誤 C3097
ms.date: 11/04/2016
f1_keywords:
- C3097
helpviewer_keywords:
- C3097
ms.assetid: b24bd8f8-e04f-4fbb-be57-4feb9165572e
ms.openlocfilehash: 8e83a92911e40df099ff5986d13dd44bd117d92d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452763"
---
# <a name="compiler-error-c3097"></a>編譯器錯誤 C3097

'attribute': 屬性必須以 'assembly:' 或 'module:' 設定範圍

不正確地使用了全域屬性。

如需詳細資訊，請參閱 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3097。

```
// C3097.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All, AllowMultiple = true)]
public ref class Attr : public Attribute {
public:
   Attr(int t) : m_t(t) {}
   int m_t;
};

[Attr(10)];   // C3097
[assembly:Attr(10)];   // OK

[Attr(10)]   // OK
public ref class MyClass {};
```