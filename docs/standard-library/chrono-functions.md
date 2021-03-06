---
title: '&lt;chrono&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: 5aadf776cc25e22a40ed75f854481dff63cce4bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597492"
---
# <a name="ltchronogt-functions"></a>&lt;chrono&gt; 函式

||||
|-|-|-|
|[duration_cast](#duration_cast)|[time_point_cast](#time_point_cast)|

## <a name="duration_cast"></a>  duration_cast

將 `duration` 物件轉換為指定的類型。

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```

### <a name="return-value"></a>傳回值

`To` 類型的 `duration` 物件，代表時間間隔 `Dur`，如果必須符合目標類型則會截斷。

### <a name="remarks"></a>備註

如果 `To` 是 `duration` 的具現化，此函式不會參與多載解析。

## <a name="time_point_cast"></a>  time_point_cast

將 [time_point](../standard-library/time-point-class.md) 物件轉換為指定的類型。

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);
```

### <a name="return-value"></a>傳回值

具有 `To` 類型之持續時間的 `time_point` 物件。

### <a name="remarks"></a>備註

除非 `To` 是 [duration](../standard-library/duration-class.md) 的具現化，否則此函式不會參與多載解析。

## <a name="see-also"></a>另請參閱

[\<chrono>](../standard-library/chrono.md)<br/>
