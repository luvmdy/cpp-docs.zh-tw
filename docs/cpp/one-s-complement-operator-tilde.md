---
title: '一個&#39;s 補數運算子: ~'
ms.date: 11/04/2016
f1_keywords:
- "~"
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: d8fb8ca56932669ff85646f2aa0c10691122013b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469770"
---
# <a name="one39s-complement-operator-"></a>一個&#39;s 補數運算子: ~

## <a name="syntax"></a>語法

```
~ cast-expression
```

## <a name="remarks"></a>備註

一補數運算子 (`~`)，有時稱為「位元補數」運算子，它會產生其運算元的位元 1 補數。 也就是說，運算元中是 1 的每個位元，在結果中都是 0。 反之，運算元中是 0 的每個位元，在結果中都是 1。 一補數運算子的運算元必須是整數類資料類型。

## <a name="operator-keyword-for-"></a>~ 的運算子關鍵字

**Compl**運算子是相等的文字`~`。 有兩種方式來存取**compl**在程式中的運算子： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md)。

## <a name="example"></a>範例

```cpp
// expre_One_Complement_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main () {
   unsigned short y = 0xFFFF;
   cout << hex << y << endl;
   y = ~y;   // Take one's complement
   cout << hex << y << endl;
}
```

在這個範例中，指派至 `y` 的新值是不帶正負號的值 0xFFFF 或 0x0000 的 1 補數。

整數運算元上會執行整數提升，且結果類型是運算元提升後的類型。 請參閱[標準轉換](standard-conversions.md)如需如何執行提升的詳細資訊。

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[一元算術運算子](../c-language/unary-arithmetic-operators.md)