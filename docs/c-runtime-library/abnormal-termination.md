---
title: _abnormal_termination
ms.date: 11/04/2016
apiname:
- _abnormal_termination
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: 231a5a521d9e234d3e31e6ccdbe98b207a89b3eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433536"
---
# <a name="abnormaltermination"></a>_abnormal_termination

指出當系統正在執行終止處理常式的內部清單時，是否輸入 [try-finally 陳述式](../cpp/try-finally-statement.md)的 `__finally` 區塊。

## <a name="syntax"></a>語法

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>傳回值

**true** 如果系統「回溯」堆疊則為 ，否則為 **false**。

## <a name="remarks"></a>備註

這是用來管理回溯例外狀況的內部函式，不是從使用者程式碼呼叫。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>請參閱

[try-finally 陳述式](../cpp/try-finally-statement.md)