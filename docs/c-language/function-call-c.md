---
title: 函式呼叫 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: 46e010ed625e23aa6c21b8c78280b714c68582b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478113"
---
# <a name="function-call-c"></a>函式呼叫 (C)

「函式呼叫」是運算式，其中包含所呼叫函式的名稱，或函式指標的值，以及傳遞至函式的選擇性引數。

## <a name="syntax"></a>語法

*postfix-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**

*argument-expression-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *assignment-expression*

*postfix-expression* 必須評估為函式位址 (例如，函式識別項或函式指標的值)，而 *argument-expression-list* 是運算式的清單 (以逗號分隔)，其中的值 (引數) 會傳遞至函式。 *argument-expression-list* 引數可以是空的。

函式呼叫運算式具有函式傳回值的值和類型。 函式不能傳回陣列類型的物件。 如果函式的傳回類型是 `void` (也就是說，函式宣告為永不傳回值)，則函式呼叫運算式也會具有 `void` 類型  (如需詳細資訊，請參閱[函式呼叫](../c-language/function-calls.md))。

## <a name="see-also"></a>請參閱

[函式呼叫運算子：()](../cpp/function-call-operator-parens.md)