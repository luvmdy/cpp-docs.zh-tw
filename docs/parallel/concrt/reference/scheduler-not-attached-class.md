---
title: scheduler_not_attached 類別
ms.date: 11/04/2016
f1_keywords:
- scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached::scheduler_not_attached
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
ms.openlocfilehash: 159202445f95e8fbac93902dec43fc0f99180e8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560663"
---
# <a name="schedulernotattached-class"></a>scheduler_not_attached 類別

這個類別描述作業需要將排程器附加至目前內容，而卻沒有這麼做時所擲回的例外狀況。

## <a name="syntax"></a>語法

```
class scheduler_not_attached : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[scheduler_not_attached](#ctor)|多載。 建構 `scheduler_not_attached` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`scheduler_not_attached`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> scheduler_not_attached

建構 `scheduler_not_attached` 物件。

```
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```

### <a name="parameters"></a>參數

*訊息 （_m)*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)
