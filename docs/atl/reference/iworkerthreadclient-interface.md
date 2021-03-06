---
title: IWorkerThreadClient 介面
ms.date: 11/04/2016
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
ms.openlocfilehash: 22ea136dd91a514ff10e13cd02b796565b7b0307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523628"
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient 介面

`IWorkerThreadClient` 是用戶端所實作的介面[CWorkerThread](../../atl/reference/cworkerthread-class.md)類別。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
__interface IWorkerThreadClient
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CloseHandle](#closehandle)|實作此方法以關閉這個物件相關聯的控制代碼。|
|[Execute](#execute)|實作這個方法，這個物件相關聯的控制代碼會變成收到訊號時執行程式碼。|

## <a name="remarks"></a>備註

當您擁有需要回應變成收到訊號的控制代碼的背景工作執行緒上執行的程式碼時，請實作這個介面。

## <a name="requirements"></a>需求

**標頭：** atlutil.h

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

實作此方法以關閉這個物件相關聯的控制代碼。

```
HRESULT CloseHandle(HANDLE  hHandle);
```

### <a name="parameters"></a>參數

*hHandle*<br/>
關閉控制代碼。

### <a name="return-value"></a>傳回值

在成功或失敗的錯誤 HRESULT 傳回 S_OK。

### <a name="remarks"></a>備註

控制代碼傳遞給這個方法是先前物件相關聯的呼叫所[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

### <a name="example"></a>範例

下列程式碼顯示的簡單實作`IWorkerThreadClient::CloseHandle`。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

實作這個方法，這個物件相關聯的控制代碼會變成收到訊號時執行程式碼。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>參數

*dwParam*<br/>
User 參數。

*hObject*<br/>
變成已收到訊號的控制代碼。

### <a name="return-value"></a>傳回值

在成功或失敗的錯誤 HRESULT 傳回 S_OK。

### <a name="remarks"></a>備註

控制代碼和 DWORD/指標傳遞給這個方法是先前物件相關聯的呼叫所[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

### <a name="example"></a>範例

下列程式碼顯示的簡單實作`IWorkerThreadClient::Execute`。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)<br/>
[CWorkerThread 類別](../../atl/reference/cworkerthread-class.md)
