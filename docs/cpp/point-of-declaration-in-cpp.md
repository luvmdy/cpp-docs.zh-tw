---
title: C++ 中的宣告點
ms.date: 11/04/2016
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
ms.openlocfilehash: d6cb4c3813d88c8b29fbcb2e0827805f406e6c81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560650"
---
# <a name="point-of-declaration-in-c"></a>C++ 中的宣告點

名稱會視為在緊接著它的宣告子之後、但是在它的 (選擇性) 初始設定式之前宣告  (如需宣告子的詳細資訊，請參閱[宣告和定義](declarations-and-definitions-cpp.md)。)

請考量以下範例：

```cpp
// point_of_declaration1.cpp
// compile with: /W1
double dVar = 7.0;
int main()
{
   double dVar = dVar;   // C4700
}
```

宣告點一樣*之後*，則本機`dVar`會初始化為 7.0，全域變數的值`dVar`。 不過，由於並不是這種情況，因此 `dVar` 會初始化為未定義的值。

## <a name="see-also"></a>另請參閱

[範圍](../cpp/scope-visual-cpp.md)