---
title: 編譯器錯誤 C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: d1a5632328c00ca2dcd03519d03fbdb648776a51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637875"
---
# <a name="compiler-error-c2483"></a>編譯器錯誤 C2483

>'*識別碼*': 建構函式或解構函式的物件不可以宣告為 'thread'

此錯誤訊息是在 Visual Studio 2015 和更新版本已過時。 在舊版中，變數則是使用宣告`thread`屬性無法使用建構函式或其他需要執行階段評估的運算式進行初始化。 靜態運算式，才能初始化`thread`資料。

## <a name="example"></a>範例

下列範例會在 Visual Studio 2013 和舊版中產生 C2483。

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>另請參閱

[thread](../../cpp/thread.md)