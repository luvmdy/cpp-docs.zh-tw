---
title: 編譯器錯誤 C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: e8f82ed4ce8ad77a22961a42c8e9a256e6f647db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535131"
---
# <a name="compiler-error-c2461"></a>編譯器錯誤 C2461

> '*類別*': 建構函式語法遺漏型式參數

此類別的建構函式未指定任何的型式參數。 建構函式宣告必須指定的型式參數清單。 清單可以是空的。

若要修正此問題，請新增一組括號之後的宣告*類別*:: **類別*。

## <a name="example"></a>範例

下列範例示範如何修正問題 C2461:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```