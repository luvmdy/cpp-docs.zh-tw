---
title: 編譯器錯誤 C3880
ms.date: 11/04/2016
f1_keywords:
- C3880
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
ms.openlocfilehash: 60b96a9e704215ec1cbbab63eb77ca5d43ccb627
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626937"
---
# <a name="compiler-error-c3880"></a>編譯器錯誤 C3880

'var': 不可以是常值資料成員

型別[常值](../../windows/literal-cpp-component-extensions.md)必須是屬性，或編譯時期轉換成下列類型之一：

- 整數類資料類型

- 字串

- 整數或基礎類型的列舉

下列範例會產生 C3880:

```
// C3880.cpp
// compile with: /clr /c
ref struct Y1 {
   literal System::Decimal staticConst1 = 10;   // C3880
   literal int staticConst2 = 10;   // OK
};
```