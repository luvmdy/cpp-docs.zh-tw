---
title: 可繫結 （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.bindable
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
ms.openlocfilehash: 08ecd3e242d1e3601f7a5a3ea54c51a679dca97a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664148"
---
# <a name="bindable"></a>bindable

表示支援資料繫結的屬性。

## <a name="syntax"></a>語法

```cpp
[bindable]
```

## <a name="remarks"></a>備註

**可繫結**c + + 屬性具有相同的功能[可繫結](/windows/desktop/Midl/bindable)MIDL 屬性。 您可以利用定義的屬性上使用它[propget](propget.md)， [propput](propput.md)，或[propputref](propputref.md)屬性，或者您可以手動定義的可繫結的方法。

下列的 MFC 範例示範如何使用**可繫結**:

- [控制項的範例： MFC 為基礎的 ActiveX 控制項](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [CIRC 範例： ActiveX 控制項](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

- [工具提示與說明 TESTHELP 範例： ActiveX 控制項](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/controls)

## <a name="example"></a>範例

下列程式碼會示範如何使用**可繫結**屬性：

```cpp
// cpp_attr_ref_bindable.cpp
// compile with: /LD
#include <windows.h>
[
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"), dispinterface, helpstring("property demo Interface")
]
__interface IPropDemo : IDispatch {

   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();
};

[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)