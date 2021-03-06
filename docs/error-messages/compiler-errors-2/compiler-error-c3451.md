---
title: 編譯器錯誤 C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 041c0c22b7ae842073bfd6656d9cbb3b2a20af9c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430052"
---
# <a name="compiler-error-c3451"></a>編譯器錯誤 C3451

'attribute': 無法套用到 'type' 的非受控的屬性

C + + 屬性無法套用至 CLR 型別。 請參閱[c + + 屬性參考](../../windows/cpp-attributes-reference.md)如需詳細資訊。

如需詳細資訊，請參閱 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。

針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致此錯誤： [uuid](../../windows/uuid-cpp-attributes.md)屬性不再允許使用者定義的屬性，使用 CLR 程式設計上。 請改用 <xref:System.Runtime.InteropServices.GuidAttribute>。

## <a name="example"></a>範例

下列範例會產生 C3451。

```
// C3451.cpp
// compile with: /clr /c
using namespace System;
[ attribute(AttributeTargets::All) ]
public ref struct MyAttr {};

[ MyAttr, helpstring("test") ]   // C3451
// try the following line instead
// [ MyAttr ]
public ref struct ABC {};
```