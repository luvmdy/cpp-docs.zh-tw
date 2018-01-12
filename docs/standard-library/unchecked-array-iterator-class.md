---
title: "unchecked_array_iterator 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdext::unchecked_array_iterator
dev_langs: C++
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c36cadfa048a51c43b4e71f0e03b699434021dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator 類別
`unchecked_array_iterator` 類別可讓您將陣列或指標包裝在未檢查的迭代器中。 使用這個類別做為原始指標或陣列的包裝函式 (使用 [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator) 函式)，做為管理未檢查指標警告的目標方式，而非全域的關閉這些警告訊息。 如果可能，請優先使用這個類別的已檢查版本 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)。  
  
> [!NOTE]
>  這個類別是 C++ 標準程式庫的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。  
  
## <a name="syntax"></a>語法  
  
```
template <class Iterator>  
class unchecked_array_iterator;
```  
  
## <a name="remarks"></a>備註  
 這個類別是在 [stdext](../standard-library/stdext-namespace.md) 命名空間中定義的。  
  
 這是 [checked_array_iterator 類別](../standard-library/checked-array-iterator-class.md)的未檢查版本，並支援所有相同的多載和成員。 如需已檢查的迭代器功能的詳細資訊和程式碼範例，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<iterator>  
  
 **命名空間：** stdext  
  
## <a name="see-also"></a>請參閱  
 [\<iterator>](../standard-library/iterator.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)


