---
title: 嚴重錯誤 C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: fbba87cea05d666d6dc3a385ca1fe52e143fdb5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648678"
---
# <a name="fatal-error-c1352"></a>嚴重錯誤 C1352

函式 'function' (位於模組 'file' 中) 的 MSIL 無效或損毀

.netmodule 已傳遞至編譯器，但編譯器偵測到檔案損毀。  請要求產生 .netmodule 的人員調查。

編譯器不會檢查所有類型之損毀的 .netmodule 檔案。  但會確認函式中的所有控制路徑都包含 return 陳述式。

如需詳細資訊，請參閱 [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。