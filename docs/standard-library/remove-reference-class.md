---
title: "remove_reference 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::remove_reference
dev_langs: C++
helpviewer_keywords:
- remove_reference class
- remove_reference
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63434baf27e1b2f246d52bb3fd66977c58bbff64
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="removereference-class"></a>remove_reference 類別
從類型建立非參考類型。  
  
## <a name="syntax"></a>語法  
  
```  
template <class T>  
struct remove_reference;  
 
template <class T>  
using remove_reference_t = typename remove_reference<T>::type;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要修改的類型。  
  
## <a name="remarks"></a>備註  
 `remove_reference<T>` 執行個體儲存修改的類型，如果 `T1` 的格式為 `T`，類型為 `T1&`，否則為 `T`。  
  
## <a name="example"></a>範例  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_reference_t<int&> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_reference_t<int&> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
remove_reference_t<int&> == int  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)   
 [add_lvalue_reference 類別](../standard-library/add-lvalue-reference-class.md)