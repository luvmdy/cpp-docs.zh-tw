---
title: _get_printf_count_output
ms.date: 11/04/2016
apiname:
- _get_printf_count_output
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: 477e4a9e987f27bd70b9707e91b9ea9d84b69993
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610625"
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output

指出是否[printf、 _printf_l、 wprintf、 _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-系列函式支援 **%n**格式。

## <a name="syntax"></a>語法

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>傳回值

如果是非零 **%n**支援，0 **%n**不支援。

## <a name="remarks"></a>備註

如果 **%n**不是支援 （預設值），遇到 **%n**格式字串中的任一**printf**函式會叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果 **%n**已啟用支援 (請參閱[_set_printf_count_output](set-printf-count-output.md)) 然後 **%n**中所述的行為[格式規格語法： printf 和 wprintf函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱[_set_printf_count_output](set-printf-count-output.md)的範例。

## <a name="see-also"></a>另請參閱

[_set_printf_count_output](set-printf-count-output.md)<br/>
