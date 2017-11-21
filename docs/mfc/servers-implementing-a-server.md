---
title: "伺服器： 實作伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ed4ca1b131e56b2735b3a6e4ba408f3ad79b8de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="servers-implementing-a-server"></a>伺服器：實作伺服器
本文說明 MFC 應用程式精靈建立視覺化編輯伺服器應用程式的程式碼。 如果您不使用應用程式精靈，這篇文章會列出，您必須撰寫程式碼以實作伺服器應用程式的區域。  
  
 如果您使用應用程式精靈建立新的伺服器應用程式，它會為您提供大量的伺服器專屬的程式碼。 如果您要將視覺化編輯伺服器功能加入現有的應用程式，您必須複製應用程式精靈會新增必要的伺服器程式碼的其餘部分之前所提供的程式碼。  
  
 應用程式精靈提供的伺服器程式碼分成數種類別：  
  
-   定義伺服器資源：  
  
    -   伺服器正在編輯內嵌項目在它自己的視窗時，使用功能表資源。  
  
    -   使用的伺服器時作用中的位置中的功能表和工具列資源。  
  
     如需有關這些資源的詳細資訊，請參閱[功能表和資源： 伺服器加入](../mfc/menus-and-resources-server-additions.md)。  
  
-   定義項目類別衍生自`COleServerItem`。 如需伺服器項目的詳細資訊，請參閱[伺服器： 伺服器項目](../mfc/servers-server-items.md)。  
  
-   變更的文件類別的基底類別`COleServerDoc`。 如需詳細資訊，請參閱[伺服器： 實作伺服器文件](../mfc/servers-implementing-server-documents.md)。  
  
-   定義框架視窗類別衍生自`COleIPFrameWnd`。 如需詳細資訊，請參閱[伺服器： 實作就地框架視窗](../mfc/servers-implementing-in-place-frame-windows.md)。  
  
-   在 Windows 系統註冊資料庫中建立伺服器應用程式的項目，並向 OLE 系統中註冊伺服器的新執行個體。 如需本主題的資訊，請參閱[註冊](../mfc/registration.md)。  
  
-   初始化和啟動伺服器應用程式。 如需本主題的資訊，請參閱[註冊](../mfc/registration.md)。  
  
 如需詳細資訊，請參閱[COleServerItem](../mfc/reference/coleserveritem-class.md)， [COleServerDoc](../mfc/reference/coleserverdoc-class.md)，和[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)中*類別庫參考*。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器](../mfc/servers.md)   
 [容器](../mfc/containers.md)   
 [功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [註冊](../mfc/registration.md)
