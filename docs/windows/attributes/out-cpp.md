---
title: out （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 15b82ddca42f9b70ac16538cea19f8aedd799c05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574439"
---
# <a name="out-c"></a>out (C++)

識別從被呼叫程序傳回至呼叫程序的指標參數 (從伺服器至用戶端)。

## <a name="syntax"></a>語法

```cpp
[out]
```

## <a name="remarks"></a>備註

**out** C++ 屬性的功能與 [out](/windows/desktop/Midl/out-idl) MIDL 屬性相同。

## <a name="example"></a>範例

請參閱 [bindable](bindable.md) 範例中 **out**的範例使用。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)