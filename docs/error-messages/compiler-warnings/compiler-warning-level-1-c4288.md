---
title: 編譯器警告 (層級 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: d8769f5663ca0bde9048e52d4579012dfccab0a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532024"
---
# <a name="compiler-warning-level-1-c4288"></a>編譯器警告 (層級 1) C4288

使用非標準擴充: 'var': 在 「 for 迴圈中宣告的迴圈控制變數範圍外使用 for 迴圈;與外部範圍中宣告衝突

進行編譯時[/Ze](../../build/reference/za-ze-disable-language-extensions.md)並 **/zc: forscope-**，在宣告的變數**的**之後已使用迴圈[的](../../cpp/for-statement-cpp.md)-迴圈範圍。 C + + 語言的 Microsoft 擴充功能可讓這個變數，以保持在範圍內，並 C4288 提醒您，不使用第一個宣告的變數。

請參閱[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)如需有關如何指定中的 Microsoft 擴充功能資訊**如**使用 /Ze 的迴圈。

下列範例會產生 C4288:

```
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```