---
title: 編譯器警告 (層級 1) C4490
ms.date: 11/04/2016
f1_keywords:
- C4490
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
ms.openlocfilehash: 89ee97a4efde6f2f9c57daf0ae769e5e12341913
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624337"
---
# <a name="compiler-warning-level-1-c4490"></a>編譯器警告 (層級 1) C4490

'override': 覆寫規範; 的用法不正確'function' 不符合基底 ref 類別方法

覆寫規範的使用方式錯誤。 比方說，您不覆寫介面函式，您可以實作它。

如需詳細資訊，請參閱 <<c0> [ 覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C4490。

```
// C4490.cpp
// compile with: /clr /c /W1

interface struct IFace {
   void Test();
};

ref struct Class1 : public IFace {
   virtual void Test() override {}   // C4490
   // try the following line instead
   // virtual void Test() {}
};
```