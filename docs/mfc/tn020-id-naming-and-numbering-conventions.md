---
title: TN020：ID 命名和編號慣例
ms.date: 11/04/2016
f1_keywords:
- vc.id
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
ms.openlocfilehash: 9e575ee99b78b8efa75096cac4559eb9aea7fd21
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518667"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020：ID 命名和編號慣例

此提示描述的識別碼命名和編號慣例 MFC 2.0 使用的資源、 命令、 字串、 控制項和子視窗。

MFC 識別碼命名和編號慣例旨在符合下列需求：

- 提供 MFC 程式庫和 MFC 應用程式所支援的 Visual c + + 資源編輯器使用一致的識別碼命名標準。 這可以方便程式設計師可以解譯的類型和原始的資源，以從其識別碼。

- 強調強式識別碼的某些型別之間的 1 對 1 關聯性。

- 符合已廣泛使用的標準來命名 Windows 中的識別碼。

- 資料分割的識別碼編號的空間。 識別碼可以指派由程式設計師、 MFC、 Windows 和 Visual c + + 編輯的資源。 適當的資料分割，將有助於避免重複的識別碼。

## <a name="the-id-prefix-naming-convention"></a>識別碼前置詞命名慣例

應用程式可能會發生數種類型的識別碼。 MFC 識別碼命名的慣例定義不同的前置詞不同的資源類型。

MFC 會使用前置詞"IDR_"，表示適用於多個資源類型的資源識別碼。 比方說，針對指定的框架視窗中，MFC 會使用相同的 「 IDR_"前置詞，表示功能表、 快速鍵、 字串和圖示的資源。 下表顯示各種不同的前置詞和其使用方式：

|前置詞|使用|
|------------|---------|
|IDR_|多個資源類型 （主要是用於功能表、 快速鍵和功能區）。|
|IDD_|若為對話方塊範本資源 (例如 IDD_DIALOG1)。|
|IDC_|適用於資料指標的資源。|
|IDI_|適用於圖示資源。|
|IDB_|若為點陣圖資源。|
|IDS_|適用於字串資源。|

對話方塊資源中，MFC 會遵循下列慣例：

|前置詞或標籤|使用|
|---------------------|---------|
|IDOK IDCANCEL|標準的推播按鈕的識別碼。|
|IDC_|其他對話方塊控制項。|

「 IDC_"前置詞，也會使用資料指標。 命名衝突通常不問題因為一般應用程式會有幾個資料指標和許多對話方塊控制項。

功能表資源中，MFC 會遵循下列慣例：

|前置詞|使用|
|------------|---------|
|IDM_|不使用 MFC 命令架構的功能表項目。|
|ID_|使用 MFC 的功能表命令的命令架構。|

請依照 MFC 命令架構的命令必須要有 ON_COMMAND 命令處理常式，且可以 ON_UPDATE_COMMAND_UI 處理常式。 如果這些命令處理常式會遵循 MFC 命令架構，它們將會正常運作是否它們繫結至功能表命令、 工具列按鈕或對話方塊列按鈕。 相同的 「 ID_"前置詞，也會顯示在程式的訊息列的功能表提示字串。 大部分的應用程式中的功能表項目應該遵循的 MFC 命令慣例。 所有標準命令 Id (例如 ID_FILE_NEW) 會遵循此慣例。

MFC 也會使用"IDP_ 」 作為一種特殊形式的字串 （而不是 「 IDS_")。 "IDP_"前置詞的字串會出現提示，也就是在訊息方塊中所使用的字串。 「 IDP_"字串可以包含"%1"和"%2"做為預留位置的程式所決定的字串。 「 IDP_"字串通常具有與其相關聯的 [說明] 主題，且 「 IDS_"字串。 "IDP_"字串一律會當地語系化，並可能不會當地語系化"IDS_"字串。

MFC 程式庫也會使用"IDW_"前置詞為一種特殊形式的控制項 Id （而不是 「 IDC_")。 這些識別碼指派給子視窗，例如檢視和分隔器的架構類別。 MFC 實作識別碼會加上"AFX_ 」。

## <a name="the-id-numbering-convention"></a>識別碼編號慣例

下表列出的特定類型之識別碼的有效範圍。 限制的一些技術實作限制，而有些則是設計來防止您的識別碼衝突與 Windows 預先定義的 Id 或 MFC 預設實作的慣例。

我們強烈建議您定義建議的範圍內的所有識別碼。 這些範圍的下限為 1，因為不會使用 0。 我們建議您使用常見的慣例，並使用 100 或 101 做為第一次的識別碼。

|前置詞|資源類型|有效範圍|
|------------|-------------------|-----------------|
|IDR_|多個|1 至 0x6FFF|
|IDD_|對話方塊範本|1 至 0x6FFF|
|IDC_、 IDI_，IDB_|游標、 圖示、 點陣圖|1 至 0x6FFF|
|IDS_ IDP_|一般的字串|1 到 0x7FFF|
|ID_|命令|0x8000 到 0xDFFF|
|IDC_|控制項|8 至 0xDFFF|

如需這些範圍限制的原因：

- 依照慣例，不使用識別碼值 0。

- Windows 實作的限制，則為 true 的資源要小於或等於 0x7FFF 的識別碼。

- MFC 的內部架構會保留這些範圍：

  - 透過 0x7FFF 0x7000 （請參閱 afxres.h）

  - 透過 0xEFFF 0xE000 （請參閱 afxres.h）

  - 16000 透過 18000 （請參閱 afxribbonres.h）

  這些範圍可能會變更在未來的 MFC 實作。

- Windows 系統的數個命令使用 0xF000 到 0xFFFF 的範圍。

- 1 到 7 的控制項 Id 被保留給標準的控制項，例如 IDOK 及 IDCANCEL。

- 0x8000 到字串的 0xFFFF 的範圍被保留給功能表會提示您輸入命令。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

