---
title: 編譯器警告 (層級 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: a542f9b6bb73e561592e1e779aa6ee493612e6ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554087"
---
# <a name="compiler-warning-level-1-c4530"></a>編譯器警告 (層級 1) C4530

C + + 例外狀況處理常式使用，但回溯語意不會啟用。 指定 /EHsc

使用 c + + 例外狀況處理，但[/EHsc](../../build/reference/eh-exception-handling-model.md)未選取。

/EHsc 選項尚未啟用，都不會終結在框架中，函式執行會擲回和攔截會擲回，此函式之間的自動儲存的物件。 不過，在建立具有自動儲存的物件**嘗試**或**攔截**區塊將被終結。

下列範例會產生 C4530:

```
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

編譯範例，其中含有 /EHsc，若要解決這個警告。