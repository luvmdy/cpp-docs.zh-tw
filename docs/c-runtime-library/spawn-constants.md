---
title: spawn 常數
ms.date: 11/04/2016
f1_keywords:
- _P_NOWAIT
- _P_OVERLAY
- _P_WAIT
- _P_DETACH
- _P_NOWAITO
helpviewer_keywords:
- _P_OVERLAY constant
- P_DETACH constant
- P_OVERLAY constant
- P_NOWAIT constant
- _P_DETACH constant
- _P_NOWAIT constant
- _P_NOWAITO constant
- P_NOWAITO constant
- spawn constants
- P_WAIT constant
- _P_WAIT constant
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
ms.openlocfilehash: 1bfb13309ae4bd667a5e128300740f4c903f08be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580943"
---
# <a name="spawn-constants"></a>spawn 常數

## <a name="syntax"></a>語法

```
#include <process.h>
```

## <a name="remarks"></a>備註

`mode` 引數會決定在 spawn 作業之前及期間，呼叫處理序所採取的動作。 `mode` 可能有下列值：

|常數|意義|
|--------------|-------------|
|`_P_OVERLAY`|重疊呼叫處理序與新的處理序，會終結呼叫處理序 (與 `_exec` 呼叫的效果相同)。|
|`_P_WAIT`|暫停呼叫執行緒直到新的處理序執行完成 (同步的 `_spawn`)。|
|`_P_NOWAIT`、 `_P_NOWAITO`|同時繼續執行呼叫處理序與新的處理序 (非同步的 `_spawn`)。|
|`_P_DETACH`|繼續執行呼叫處理序，新處理序在背景執行，但無法存取主控台或鍵盤。 針對新處理序呼叫 `_cwait` 將會失敗。 這是非同步 `_spawn`。|

## <a name="see-also"></a>請參閱

[_spawn、_wspawn 函式](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)