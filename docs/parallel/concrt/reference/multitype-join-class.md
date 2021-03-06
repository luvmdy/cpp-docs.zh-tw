---
title: multitype_join 類別
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: 2fd94ef072fcab9af076fcdfa1b5c094d77f89c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547383"
---
# <a name="multitypejoin-class"></a>multitype_join 類別

`multitype_join` 傳訊區塊是多來源的單一目標傳訊區塊，會與來自其來源的不同類型訊息合併，並且為其目標提供 Tuple 合併的訊息。

## <a name="syntax"></a>語法

```
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

#### <a name="parameters"></a>參數

*T*<br/>
`tuple`之訊息的裝載類型加入且由區塊所傳播。

*_Jtype*<br/>
類型的`join`區塊，這是，可能是`greedy`或 `non_greedy`

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|類型別名`T`。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[multitype_join](#ctor)|多載。 建構 `multitype_join` 傳訊區塊。|
|[~ multitype_join 解構函式](#dtor)|終結`multitype_join`傳訊區塊。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[accept](#accept)|接受的訊息，由此`multitype_join`區塊中，將擁有權傳送給呼叫者。|
|[acquire_ref](#acquire_ref)|取得此參考計數`multitype_join`傳訊區塊，以防止刪除。|
|[consume](#consume)|會使用先前所提供訊息`multitype_join`傳訊區塊和目標，將擁有權傳送給呼叫者已成功保留。|
|[link_target](#link_target)|將目標區塊連結至這個`multitype_join`傳訊區塊。|
|[release](#release)|釋放先前成功的訊息保留。|
|[release_ref](#release_ref)|釋放此參考計數`multiple_join`傳訊區塊。|
|[reserve](#reserve)|保留先前由此訊息`multitype_join`傳訊區塊。|
|[unlink_target](#unlink_target)|取消連結的目標區塊，從這個`multitype_join`傳訊區塊。|
|[unlink_targets](#unlink_targets)|取消連結所有的目標，從這個`multitype_join`傳訊區塊。 (覆寫[isource:: Unlink_targets](isource-class.md#unlink_targets)。)|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="accept"></a> 接受

接受的訊息，由此`multitype_join`區塊中，將擁有權傳送給呼叫者。

```
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`提供的`message`物件。

*_PTarget*<br/>
正在呼叫的目標區塊的指標`accept`方法。

### <a name="return-value"></a>傳回值

指標，呼叫者現在擁有的訊息。

##  <a name="acquire_ref"></a> acquire_ref

取得此參考計數`multitype_join`傳訊區塊，以防止刪除。

```
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
正在呼叫這個方法的目標區塊的指標。

### <a name="remarks"></a>備註

這個方法會呼叫`ITarget`物件所要連結到這個來源期間，`link_target`方法。

##  <a name="consume"></a> 使用

會使用先前所提供訊息`multitype_join`傳訊區塊和目標，將擁有權傳送給呼叫者已成功保留。

```
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的保留`message`物件。

*_PTarget*<br/>
正在呼叫的目標區塊的指標`consume`方法。

### <a name="return-value"></a>傳回值

指標`message`物件，呼叫者現在會有的擁有權。

### <a name="remarks"></a>備註

`consume`方法是類似`accept`，但必須一律加上呼叫`reserve`傳回**true**。

##  <a name="link_target"></a> link_target

將目標區塊連結至這個`multitype_join`傳訊區塊。

```
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
指標`ITarget`連結到此區塊`multitype_join`傳訊區塊。

##  <a name="ctor"></a> multitype_join

建構 `multitype_join` 傳訊區塊。

```
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>參數

*_Tuple*<br/>
此 `tuple` 傳訊區塊的 `multitype_join` 來源。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

*_Join*<br/>
作為複製來源處的 `multitype_join` 傳訊區塊。 請注意，原始物件會被遺棄，使其成為移動建構函式。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

移動建構函式不會在鎖定下執行，這表示使用者必須確認在移動時沒有任何輕量工作在執行中。 否則，可能發生許多競爭情況，導致例外狀況或不一致的狀態。

##  <a name="dtor"></a> ~ multitype_join

終結`multitype_join`傳訊區塊。

```
~multitype_join();
```

##  <a name="release"></a> 版本

釋放先前成功的訊息保留。

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的`message`物件被釋放。

*_PTarget*<br/>
正在呼叫的目標區塊的指標`release`方法。

##  <a name="release_ref"></a> release_ref

釋放此參考計數`multiple_join`傳訊區塊。

```
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
正在呼叫這個方法的目標區塊的指標。

### <a name="remarks"></a>備註

這個方法會呼叫`ITarget`要從這個來源取消連結的物件。 來源區塊允許釋放任何資源保留給目標區塊。

##  <a name="reserve"></a> 保留

保留先前由此訊息`multitype_join`傳訊區塊。

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的`message`物件所保留。

*_PTarget*<br/>
正在呼叫的目標區塊的指標`reserve`方法。

### <a name="return-value"></a>傳回值

`true` 如果已成功保留訊息，`false`否則。 保留失敗可能有許多原因，包括：訊息已經保留或已由另一個目標接受、來源拒絕保留等等。

### <a name="remarks"></a>備註

在您呼叫後`reserve`，如果成功，您必須呼叫`consume`或`release`以便採取或分別放棄訊息，因此擁有。

##  <a name="unlink_target"></a> unlink_target

取消連結的目標區塊，從這個`multitype_join`傳訊區塊。

```
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
指標`ITarget`若要從這個取消連結的區塊`multitype_join`傳訊區塊。

##  <a name="unlink_targets"></a> unlink_targets

取消連結所有的目標，從這個`multitype_join`傳訊區塊。

```
virtual void unlink_targets();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[choice 類別](choice-class.md)<br/>
[join 類別](join-class.md)
