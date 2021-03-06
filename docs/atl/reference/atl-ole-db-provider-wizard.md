---
title: ATL OLE DB 提供者精靈
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.atl.provider.overview
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
ms.openlocfilehash: c01852c89d79b44bdae75b0ded9e2b8d1678cbd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441313"
---
# <a name="atl-ole-db-provider-wizard"></a>ATL OLE DB 提供者精靈

此精靈會建立構成的 OLE DB 提供者的類別。

> [!WARNING]
> 在 Visual Studio 2017 15.9 版中，此程式碼精靈已淘汰，並且將從 Visual Studio 的未來版本中移除。 使用者很少用到這個精靈。 移除此精靈不會影響 ATL 和 MFC 的一般支援。 如果您想要分享關於此項淘汰的意見反應，請填寫[此問卷](https://www.surveymonkey.com/r/QDWKKCN)。 我們非常重視您的意見反應。

## <a name="remarks"></a>備註

從 Visual Studio 2008 開始，此精靈所產生的註冊指令碼會註冊其下的 COM 元件**HKEY_CURRENT_USER**而不是**HKEY_LOCAL_MACHINE**。 若要修改此行為，請設定**為所有使用者的註冊元件**ATL 精靈的選項。

下表描述 [ATL OLE DB 提供者精靈] 的選項：

- **簡短名稱**

   輸入要建立的提供者的簡短名稱。 自動填入精靈中的其他編輯方塊，將會根據您在此處輸入。 如果您想要您可以編輯其他名稱方塊。

- **Coclass**

   Coclass 的名稱。 ProgID 的名稱會變更以符合此名稱。

- **使用屬性**

   這個選項會指定精靈是否會建立使用屬性或宣告範本的提供者類別。 當您選取此選項時，精靈會使用屬性代替樣板宣告 （如果您建立屬性化的專案，這是預設選項）。 當您清除此選項時，精靈會使用樣板宣告，而非屬性 （如果您建立未使用屬性的專案，這是預設選項）。

   如果您選取此選項，當您建立未使用屬性的專案時，精靈會警告您專案將被轉換成屬性化專案，並詢問您是否要繼續進行。

- **ProgID**

   ProgID 或以程式設計方式識別項，為您的應用程式可以使用而不是 GUID 的文字字串。 ProgID 的名稱已在表單*為 Projectname.Coclassname*。

- **版本**

   您的提供者的版本號碼。 預設為 1。

- **資料來源類別**

   資料來源的類別，格式為 C 的名稱*Shortname*來源。

- **資料來源.h 檔案**

   資料來源類別標頭檔。 您可以編輯此檔案的名稱，或選取現有的標頭檔。

- **工作階段類別**

   工作階段類別，格式為 C 的名稱*Shortname*工作階段。

- **工作階段.h 檔案**

   工作階段類別標頭檔。 您可以編輯此檔案的名稱，或選取現有的標頭檔。

- **命令類別**

   命令類別，格式為 C 的名稱*Shortname*命令。

- **命令.h 檔案**

   命令類別標頭檔。 這個名稱無法加以編輯，取決於資料列集標頭檔的名稱。

- **資料列集類別**

   資料列集類別，格式為 C 的名稱*Shortname*資料列集。

- **資料列集的.h 檔案**

   資料列集類別的標頭檔。 您可以編輯此檔案的名稱，或選取現有的標頭檔。

- **資料列集.cpp 檔**

   提供者的實作檔案。 您可以編輯此檔案的名稱，或選取現有的實作檔。

## <a name="see-also"></a>另請參閱

[ATL OLE DB 提供者](../../atl/reference/adding-an-atl-ole-db-provider.md)

