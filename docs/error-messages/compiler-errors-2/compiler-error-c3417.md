---
title: 編譯器錯誤 C3417
ms.date: 11/04/2016
f1_keywords:
- C3417
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
ms.openlocfilehash: 574af940f17c1a79472d6d20d63c9ff74d4c411e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615759"
---
# <a name="compiler-error-c3417"></a>編譯器錯誤 C3417

'member': 實值型別不能包含使用者定義的特殊成員函式

實值型別不能包含等預設執行個體建構函式、 解構函式或複製建構函式的函式。

下列範例會產生 C3517:

```
// C3417.cpp
// compile with: /clr /c
value class VC {
   VC(){}   // C3417

   // OK
   static VC(){}
   VC(int i){}
};
```