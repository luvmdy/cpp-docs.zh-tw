---
title: 編譯器錯誤 C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: 9e53d9fe273a392695212df6dbeb679822a39068
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485526"
---
# <a name="compiler-error-c3063"></a>編譯器錯誤 C3063

運算子 'operator': 所有運算元必須都具有相同的列舉類型

當使用列舉值的運算子，兩個運算元必須是列舉型別。 如需詳細資訊，請參閱 <<c0> [ 如何： 定義和使用列舉，在 C + + /cli CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3063，並示範如何修正此問題：

```
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```