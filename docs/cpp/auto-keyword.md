---
title: auto 關鍵字
ms.date: 11/04/2016
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
ms.openlocfilehash: 3477bd5033fac5b69733db5d6095c1317aac42ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607684"
---
# <a name="auto-keyword"></a>auto 關鍵字

**自動**關鍵字是宣告指定名稱。 不過，C++ 標準為此關鍵字定義了原始和修訂的意義。 Visual c + + 2010 中前,**自動**關鍵字會宣告中的變數*自動*儲存類別，也就是具有區域存留期的變數。 Visual c + + 2010 中，為起**自動**關鍵字會宣告從其宣告中的初始化運算式推算類型的變數。 [/Zc: auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md)編譯器選項可控制的意義**自動**關鍵字。

## <a name="syntax"></a>語法

```cpp
auto declarator ;
auto declarator initializer;
```

## <a name="remarks"></a>備註

定義**自動**關鍵字在 c + + 程式設計語言中，但不是以 C 程式設計語言的變更。

下列主題將描述**自動**關鍵字和對應的編譯器選項：

- [自動](../cpp/auto-cpp.md)描述的新定義**自動**關鍵字。

- [/Zc: auto （推算變數類型）](../build/reference/zc-auto-deduce-variable-type.md)描述編譯器選項會告訴編譯器的定義**自動**關鍵字，才能使用。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)