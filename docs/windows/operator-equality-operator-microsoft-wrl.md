---
title: operator== 運算子 (Microsoft::WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator==
ms.assetid: 94f383a5-17a9-40c7-9d9c-778acdc54b27
ms.openlocfilehash: 0c8a0937ec446f03ce2365ec23f9d73fc2d10a31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451541"
---
# <a name="operator-operator-microsoftwrl"></a>operator== 運算子 (Microsoft::WRL)

等號比較運算子[ComPtr](../windows/comptr-class.md)並[ComPtrRef](../windows/comptrref-class.md)物件。

## <a name="syntax"></a>語法

```cpp
WRL_NOTHROW bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);
WRL_NOTHROW bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
WRL_NOTHROW bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);
WRL_NOTHROW bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);
WRL_NOTHROW bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);
WRL_NOTHROW bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>參數

*a*<br/>
左物件。

*b*<br/>
右物件。

## <a name="return-value"></a>傳回值

**真**如果物件相等，否則**false**。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)