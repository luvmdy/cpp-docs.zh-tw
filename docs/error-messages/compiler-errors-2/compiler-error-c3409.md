---
title: 編譯器錯誤 C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: b6ceb6f2e8700a5459dbd01db443ef90de314b5e
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330082"
---
# <a name="compiler-error-c3409"></a>編譯器錯誤 C3409

> 不允許空白的屬性區塊

## <a name="remarks"></a>備註

方括號做為編譯器所解譯[屬性](../../windows/cpp-attributes-reference.md)區塊，但沒有屬性找不到。

當您使用方括號做為 lambda 運算式定義的一部分時，編譯器可能會產生此錯誤。 當編譯器無法判斷方括號是否定義 lambda 運算式或屬性區塊的一部分時，就會發生此錯誤。 如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 如果方括號是屬性區塊的一部分：

   1. 提供在屬性區塊中的一或多個屬性。

   1. 移除屬性區塊。

1. 如果方括號是 lambda 運算式的一部分，請確定 lambda 運算式會遵循有效的語法規則。

   如需有關 lambda 運算式語法的詳細資訊，請參閱 < [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)。

## <a name="example"></a>範例

下列範例會產生 C3409。

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

## <a name="example"></a>範例

因為 lambda 運算式會使用下列範例會產生 C3409`mutable`規格，但未提供參數清單。 編譯器無法判斷方括號是否定義 lambda 運算式或屬性區塊的一部分。

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>另請參閱

[attribute](../../windows/cpp-attributes-reference.md)<br/>
[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)