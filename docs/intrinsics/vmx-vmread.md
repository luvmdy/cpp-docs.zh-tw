---
title: __vmx_vmread
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 0a4528bed4426ce5b611e986a69f4b0b8c750548
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499091"
---
# <a name="vmxvmread"></a>__vmx_vmread

**Microsoft 專屬**

從目前的虛擬機器控制結構 (VMCS) 讀取指定的欄位，並將它放在指定的位置。

## <a name="syntax"></a>語法

```
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*欄位*|[in]要讀取的 VMCS 欄位。|
|*FieldValue*|[in]指標的位置來儲存值讀取所指定的 VMCS 欄位`Field`參數。|

## <a name="return-value"></a>傳回值

|值|意義|
|-----------|-------------|
|0|作業成功。|
|1|作業失敗，在目前 VMCS的 `VM-instruction error field` 中有擴充狀態。|
|2|作業失敗，無可用的狀態。|

## <a name="remarks"></a>備註

`__vmx_vmread` 函式相當於 `VMREAD` 機器指令。 值`Field`參數是 Intel 文件中所述的編碼的欄位索引。 如需詳細資訊，搜尋文件 < Intel 虛擬化技術規格的 IA-32 Intel 架構 >、 文件編號 C97063-002，位於[Intel Corporation](https://software.intel.com/articles/intel-sdm)網站的 url，然後參閱該文件的附錄 C.

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`__vmx_vmread`|X64|

**標頭檔** \<intrin.h >

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)