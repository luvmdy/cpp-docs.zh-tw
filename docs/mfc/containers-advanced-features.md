---
title: "容器： 進階功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4e79b1c88996e835a907129fa5810d4c4dca0770
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="containers-advanced-features"></a>容器：進階功能
本文描述將選擇性進階功能合併至現有容器應用程式中的必要步驟。 這些功能包括：  
  
-   [為容器和伺服器應用程式](#_core_creating_a_container_server_application)  
  
-   [內嵌物件之 OLE 連結](#_core_links_to_embedded_objects)  
  
##  <a name="_core_creating_a_container_server_application"></a>建立容器/伺服器應用程式  
 容器/伺服器應用程式是可同時做為容器和伺服器的應用程式。 Microsoft Word for Windows 就是這種應用程式的範例。 您可以將 Word for Windows 文件內嵌於其他應用程式中，也可以在 Word for Windows 文件中內嵌項目。 將您的容器應用程式修改成可同時做為容器和完整伺服器的程序 (您無法建立容器/迷你伺服器應用程式的組合)，類似建立完整伺服器的程序。  
  
 發行項[伺服器： 實作伺服器](../mfc/servers-implementing-a-server.md)列出實作伺服器應用程式所需的工作數目。 如果您將容器應用程式轉換成容器/伺服器應用程式，則需要執行一些相同的工作，將程式碼加入至容器。 以下列出一些重要的考量：  
  
-   應用程式精靈所建立的容器程式碼已初始化 OLE 子系統。 您不需要變更或加入任何提供支援的項目。  
  
-   只要文件類別的基底類別是 `COleDocument`，就將基底類別變更為 `COleServerDoc`。  
  
-   覆寫 `COleClientItem::CanActivate`，避免正在使用伺服器就地編輯時編輯項目。  
  
     例如，MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)有內嵌的容器/伺服器應用程式所建立的項目。 您開啟 OCLIENT 應用程式，並且就地編輯您的容器/伺服器應用程式所建立的項目。 在編輯您的應用程式項目時，您決定您要內嵌 MFC OLE 範例所建立的項目[HIERSVR](../visual-cpp-samples.md)。 若要這樣做，就無法使用就地啟用。 您必須完全開啟 HIERSVR 才能啟用這個項目。 因為 MFC 程式庫不支援這項 OLE 功能，因此覆寫 `COleClientItem::CanActivate` 可讓您檢查是否有這種情況，並防止應用程式中出現可能的執行階段錯誤。  
  
 如果您要建立新的應用程式，並且希望將它當做容器/伺服器應用程式執行，請在應用程式精靈的 [OLE 選項] 對話方塊中選擇該選項，如此就會自動建立這項支援。 如需詳細資訊，請參閱文章[概觀： 建立 ActiveX 控制項容器](../mfc/reference/creating-an-mfc-activex-control-container.md)。 如需有關 MFC 範例的詳細資訊，請參閱「MFC 範例」。  
  
 請注意，您無法將 MDI 應用程式插入至本身。 做為容器/伺服器的應用程式無法插入至本身，除非它是 SDI 應用程式。  
  
##  <a name="_core_links_to_embedded_objects"></a>內嵌物件連結  
 [內嵌物件的連結] 功能可讓使用者建立包含容器應用程式內部內嵌物件之 OLE 連結的文件。 例如，在文書處理器中建立包含內嵌試算表的文件。 如果您的應用程式支援內嵌物件連結，就可以將連結貼入文書處理器文件中包含的試算表內。 這項功能可讓您的應用程式使用試算表中包含的資訊，而不需要知道文書處理器從哪裡取得該資訊。  
  
#### <a name="to-link-to-embedded-objects-in-your-application"></a>連結至應用程式中的內嵌物件  
  
1.  從 `COleLinkingDoc` 衍生您的文件類別，而不要從 `COleDocument` 衍生。  
  
2.  建立 OLE 類別 ID (**CLSID**) 使用 OLE 開發工具所包含的類別 ID 產生器的應用程式。  
  
3.  在 OLE 中註冊應用程式。  
  
4.  建立 `COleTemplateServer` 物件做為應用程式類別的成員。  
  
5.  在您的應用程式類別的 `InitInstance` 成員函式中，執行下列動作：  
  
    -   藉由呼叫物件的 `COleTemplateServer` 成員函式，將 `ConnectTemplate` 物件連接至您的文件範本。  
  
    -   呼叫**coletemplateserver:: Registerall**成員函式，以向 OLE 系統中的所有類別物件。  
  
    -   呼叫 `COleTemplateServer::UpdateRegistry`。 如果應用程式啟動時並未帶有 "/Embedded" 參數，則 `UpdateRegistry` 的唯一參數應該是 `OAT_CONTAINER`。 這樣會將應用程式註冊為可支援內嵌物件連結的容器。  
  
         如果應用程式啟動時帶有 "/Embedded" 參數，則不應該顯示其主視窗，就像伺服器應用程式一樣。  
  
 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)實作這項功能。 如需有關如何進行這項作業的範例，請參閱本範例應用程式的 OCLIENT.CPP 檔案中的 `InitInstance` 函式。  
  
## <a name="see-also"></a>請參閱  
 [容器](../mfc/containers.md)   
 [伺服器](../mfc/servers.md)
