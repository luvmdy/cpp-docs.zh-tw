---
title: MFC 中的例外狀況處理
ms.date: 11/04/2016
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: 4b520072bd0c07e261f2cf4baf51d7ea3d14a5ab
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694552"
---
# <a name="exception-handling-in-mfc"></a>MFC 中的例外狀況處理

這篇文章說明在 MFC 中的例外狀況處理機制。 可使用兩種機制：

- C + + 例外狀況，可以使用 MFC 3.0 版和更新版本

- MFC 例外狀況巨集，可在 MFC 1.0 版及更新版本

如果您要撰寫使用 MFC 的新應用程式，您應該使用 c + + 機制。 如果您現有的應用程式已廣泛使用此機制，您可以使用巨集為基礎的機制。

您可以輕易地轉換現有的程式碼，而非 MFC 例外狀況巨集使用 c + + 例外狀況。 一文中說明轉換您的程式碼和指導方針這樣的好處[例外狀況： 從 MFC 例外狀況巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)。

如果您已開發的應用程式使用 MFC 例外狀況巨集，您可以繼續在新的程式碼中使用 c + + 例外狀況時，您現有的程式碼中使用這些巨集。 發行項[例外狀況： 3.0 版例外狀況巨集變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)這樣會提供指導方針。

> [!NOTE]
>  若要啟用 c + + 例外狀況處理程式碼中，選取 C/c + + 專案的資料夾中的 [程式碼產生] 頁面上的 啟用 c + + 例外狀況[屬性頁](../ide/property-pages-visual-cpp.md)對話方塊中或使用[/EHsc](../build/reference/eh-exception-handling-model.md)編譯器選項。

本文章涵蓋下列主題：

- [使用例外狀況的時機](#_core_when_to_use_exceptions)

- [MFC 例外狀況支援](#_core_mfc_exception_support)

- [深入了解例外狀況](#_core_further_reading_about_exceptions)

##  <a name="_core_when_to_use_exceptions"></a> 使用例外狀況的時機

在程式執行期間呼叫的函式時，可能會發生三種類別的結果： 正常執行、 錯誤的執行或不正常執行。 以下說明每個類別目錄。

- 正常執行

   此函式可能會正常執行，並傳回。 某些函數會傳回結果的程式碼，呼叫者，這表示函式的結果。 可能的結果代碼嚴格定義的函式，並代表可能的結果，函式的範圍。 結果碼可表示成功或失敗，或甚至可以指出特定類型的預期正常範圍內的失敗。 例如，檔案狀態函式可以傳回表示該檔案不存在的程式碼。 請注意，因為結果碼可代表許多預期的結果之一，不會使用詞彙 「 錯誤碼 」。

- 錯誤的執行

   呼叫端會傳遞至函式的引數的一些錯誤或不適當的內容中呼叫函式。 這種情況會導致錯誤，並應判斷提示程式開發期間所偵測到。 (如需有關判斷提示的詳細資訊，請參閱 < [C/c + + 判斷提示](/visualstudio/debugger/c-cpp-assertions)。)

- 異常的執行

   異常的執行包含的情況下，外部程式的控制項，例如低記憶體或 I/O 錯誤的條件會影響函式的結果。 異常的情況下應該由攔截和擲回例外狀況處理。

使用例外狀況是特別適合不正常執行。

##  <a name="_core_mfc_exception_support"></a> MFC 例外狀況支援

不論您直接使用 c + + 例外狀況，或是使用 MFC 例外狀況巨集，您將使用[CException 類別](../mfc/reference/cexception-class.md)或`CException`-衍生的 framework，或您的應用程式可能會擲回的物件。

下表顯示由 MFC 提供的預先定義的例外狀況。

|Exception 類別|意義|
|---------------------|-------------|
|[CMemoryException 類別](../mfc/reference/cmemoryexception-class.md)|記憶體不足|
|[CFileException 類別](../mfc/reference/cfileexception-class.md)|檔案例外狀況|
|[CArchiveException 類別](../mfc/reference/carchiveexception-class.md)|封存/序列化例外狀況|
|[CNotSupportedException 類別](../mfc/reference/cnotsupportedexception-class.md)|不支援的服務要求的回應|
|[CResourceException 類別](../mfc/reference/cresourceexception-class.md)|Windows 資源配置例外狀況|
|[CDaoException 類別](../mfc/reference/cdaoexception-class.md)|資料庫例外狀況 （DAO 類別）|
|[CDBException 類別](../mfc/reference/cdbexception-class.md)|資料庫例外狀況 （ODBC 類別）|
|[COleException 類別](../mfc/reference/coleexception-class.md)|OLE 例外狀況|
|[COleDispatchException 類別](../mfc/reference/coledispatchexception-class.md)|分派 (automation) 例外狀況|
|[CUserException 類別](../mfc/reference/cuserexception-class.md)|警示訊息方塊中，使用使用者的例外狀況則會擲回泛型[CException 類別](../mfc/reference/cexception-class.md)|

> [!NOTE]
>  MFC 支援 c + + 例外狀況和 MFC 例外狀況巨集。 MFC 不直接支援 Windows NT 結構化例外狀況處理常式 (SEH)，如所述[Structured Exception Handling](/windows/desktop/debug/structured-exception-handling)。

##  <a name="_core_further_reading_about_exceptions"></a> 深入了解例外狀況

下列文章會說明使用 MFC 程式庫例外狀況處理：

- [例外狀況：攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [例外狀況：檢查例外狀況內容](../mfc/exceptions-examining-exception-contents.md)

- [例外狀況：釋放例外狀況中的物件](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [例外狀況：從您自己的函式擲回例外狀況](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [例外狀況：資料庫例外狀況](../mfc/exceptions-database-exceptions.md)

- [例外狀況：OLE 例外狀況](../mfc/exceptions-ole-exceptions.md)

下列文件比較 MFC 例外狀況巨集，以 c + + 例外狀況關鍵字，並說明如何能夠調整您的程式碼：

- [例外狀況：3.0 版例外狀況巨集的變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [例外狀況：從 MFC 例外狀況巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [例外狀況：使用 MFC 巨集和 C++ 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>另請參閱

[C++ 例外狀況處理](../cpp/cpp-exception-handling.md)<br/>
[如何： 建立我自己的自訂例外狀況類別](http://go.microsoft.com/fwlink/p/?linkid=128045)

