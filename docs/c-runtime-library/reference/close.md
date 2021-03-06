---
title: _close
ms.date: 11/04/2016
apiname:
- _close
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
- _close
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
ms.openlocfilehash: faea008903136e8abdc39297672b31800ada796d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528020"
---
# <a name="close"></a>_close

關閉檔案。

## <a name="syntax"></a>語法

```C
int _close(
   int fd
);
```

### <a name="parameters"></a>參數

*fd*<br/>
參照已開啟之檔案的檔案描述元。

## <a name="return-value"></a>傳回值

**_close**會傳回 0，如果已成功關閉檔案。 傳回值為-1 表示錯誤。

## <a name="remarks"></a>備註

**_Close**函式會關閉與相關聯的檔案*fd*。

關閉檔案描述元和基礎 OS 檔案控制代碼。 因此，不需要呼叫**CloseHandle**如果檔案原開啟使用 Win32 函式**CreateFile**轉換為使用檔案描述元 **_open_osfhandle**.

這個函式會驗證它的參數。 如果*fd*是不正確的檔案描述項無效參數處理常式會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函數會傳回-1 及**errno**設為**EBADF**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_close**|\<io.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_open](open-wopen.md) 的範例。

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chsize](chsize.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[dup、dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_unlink、_wunlink](unlink-wunlink.md)<br/>
