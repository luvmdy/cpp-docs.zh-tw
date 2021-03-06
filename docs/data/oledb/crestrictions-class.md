---
title: CRestrictions 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: 95517931f3156c4850e07c78910ccbffff424faa
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556513"
---
# <a name="crestrictions-class"></a>CRestrictions 類別

泛型類別，可讓您指定的結構描述資料列限制。

## <a name="syntax"></a>語法

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>參數

*T*<br/>
用來存取子類別。

*nRestrictions*<br/>
結構描述資料列的限制資料行數目。

*pguid*<br/>
結構描述的 GUID 指標。

## <a name="requirements"></a>需求

**標頭：** atldbsch.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[開啟](#open)|傳回結果集，根據使用者提供的限制。|

## <a name="open"></a> Crestrictions:: Open

傳回結果集，根據使用者提供的限制。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>參數

*工作階段*<br/>
[in]指定用來連接到資料來源的現有工作階段物件。

*lpszParam*<br/>
[in]在 結構描述資料列上指定的限制。

*bBind*<br/>
[in]指定是否要自動繫結資料行對應。 預設值是 **，則為 true**，因而導致自動繫結的資料行對應。 設定*bBind*要**false**可防止自動繫結的資料行對應，讓您以手動方式可以繫結。 （手動繫結是 OLAP 使用者特別感興趣的）。

### <a name="return-value"></a>傳回值

其中一個標準的 HRESULT 值。

### <a name="remarks"></a>備註

您可以指定最多七個限制的結構描述資料列集。

請參閱[IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85))如每個結構描述資料列集上定義的限制相關資訊。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)