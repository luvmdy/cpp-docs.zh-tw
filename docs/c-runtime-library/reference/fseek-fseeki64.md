---
title: fseek、_fseeki64
ms.date: 11/04/2016
apiname:
- _fseeki64
- fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: e5f775eab370f8f4a3b6a5c1d7f0918ec7efa3ff
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331083"
---
# <a name="fseek-fseeki64"></a>fseek、_fseeki64

將檔案指標移至指定的位置。

## <a name="syntax"></a>語法

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

*offset*<br/>
從 *origin* 位移的位元組數目。

*origin*<br/>
初始位置。

## <a name="return-value"></a>傳回值

如果成功， **fseek**並 **_fseeki64**會傳回 0。 否則，它會傳回非零值。 在無法搜尋的裝置上，傳回的值為未定義。 如果*資料流*為 null 指標，或如果*原點*不是其中一個允許的值，如下所述**fseek**並 **_fseeki64**叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**要**EINVAL**並傳回-1。

## <a name="remarks"></a>備註

**Fseek**並 **_fseeki64**函式之檔案指標 （若有的話） 相關聯的移動*串流*到新的位置是*位移*從位元組*原點*。 資料流的下一個作業會在新位置進行。 在開啟以供更新的資料流中，下一項作業可能是讀取或寫入。 引數*原點*必須是其中一個 STDIO 中定義下列常數。H:

|原始值|意義|
|-|-|
| **SEEK_CUR** | 檔案指標的目前位置。 |
| **SEEK_END** | 檔案結尾。 |
| **SEEK_SET** | 檔案開頭。 |

您可以使用**fseek**並 **_fseeki64**將指標重新置放任何位置在檔案中。 指標也可以放置在超過檔案結尾的位置。 **fseek**並 **_fseeki64**清除檔案結尾指標，並取消任何之前的效果[ungetc](ungetc-ungetwc.md)對呼叫*串流*。

檔案因為附加資料而開啟時，目前的檔案位置取決於最後一個 I/O 作業，而不是下一次寫入的位置。 如果開啟以供附加的檔案上尚未發生任何 I/O 作業，該檔案的位置是檔案的開頭。

以文字模式開啟的資料流**fseek**並 **_fseeki64**為有限使用，因為歸位字元復位換行轉譯可能導致**fseek**並 **_fseeki64**產生非預期的結果。 唯一**fseek**並 **_fseeki64**保證可以運作以文字模式開啟的資料流的作業：

- 相對於任何原點值，位移為 0 的搜尋。

- 搜尋從開頭的位移值的檔案從呼叫傳回[ftell](ftell-ftelli64.md)使用時**fseek**或是[_ftelli64](ftell-ftelli64.md)時使用 **_fseeki64**.

此外，在文字模式中，Ctrl+Z 會在輸入時被解譯成檔案結尾字元。 在檔案開啟供讀取/寫入時， [fopen](fopen-wfopen.md)和所有相關的常式檢查是否有 CTRL + Z 結尾的檔案，並盡可能移除它。 這是因為使用的組合**fseek**並[ftell](ftell-ftelli64.md)或 **_fseeki64**並[_ftelli64](ftell-ftelli64.md)，結尾的檔案內移動CTRL + Z 可能會造成**fseek**或是 **_fseeki64**檔案結尾附近產生不當行為。

當 CRT 開啟以位元順序標記 (BOM) 開頭的檔案時，檔案指標的位置在 BOM 之後 (也就是在檔案實際內容的開頭)。 如果您必須**fseek**檔案的開頭，使用[ftell](ftell-ftelli64.md)以取得初始位置並**fseek**給它，而不是位置 0。

此函式於執行期間鎖定其他執行緒，因此為安全執行緒。 如需非鎖定版本，請參閱 [_fseek_nolock、_fseeki64_nolock](fseek-nolock-fseeki64-nolock.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
