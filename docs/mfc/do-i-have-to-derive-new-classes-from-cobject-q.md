---
title: 我必須從 CObject 衍生新類別嗎？
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: c2361967dcfce5e46aeec65ade3d7056b362949d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636601"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>我必須從 CObject 衍生新類別嗎？

不，不用。

衍生的類別[CObject](../mfc/reference/cobject-class.md)當您需要其提供，例如序列化或動態時的功能。 許多資料類別需要序列化至檔案，因此從 `CObject` 衍生通常是不錯的作法。 類別的範例衍生自`CObject`，請參閱 < [Scribble 範例](../visual-cpp-samples.md)。

## <a name="see-also"></a>另請參閱

[CObject 類別：常見問題集](../mfc/cobject-class-frequently-asked-questions.md)
