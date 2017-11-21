---
title: "num_put 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
dev_langs: C++
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d3870564e7374d4e3faba9bc2055f04e9d2f4b63
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="numput-class"></a>num_put 類別
樣板類別，描述可以做為地區設定 facet 的物件，以控制數值轉換為類型 `CharType` 的序列。  
  
## <a name="syntax"></a>語法  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class num_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>參數  
 `CharType`  
 程式內用於編碼地區設定字元的類型。  
  
 `OutputIterator`  
 數值 put 函式將其輸出寫入其中的迭代器類型。  
  
## <a name="remarks"></a>備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[num_put](#num_put)|`num_put` 類型物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|  
|[iter_type](#iter_type)|描述輸出迭代器的類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[do_put](#do_put)|虛擬函式，呼叫以將數字轉換成 `CharType` 序列，表示為特定地區設定格式化的數字。|  
|[put](#put)|將數字轉換成 `CharType` 序列，表示為特定地區設定格式化的數字。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
##  <a name="char_type"></a>  num_put::char_type  
 類型，用來描述由地區設定使用的字元。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型與範本參數 **CharType** 同義。  
  
##  <a name="do_put"></a>  num_put::do_put  
 虛擬函式，呼叫此函式可將數字轉換成 **CharType** 序列，以代表為特定地區設定格式化的數字。  
  
```  
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    bool val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    unsigned long val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    double val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long double val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const void* val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const unsigned long long val) const;
```  
  
### <a name="parameters"></a>參數  
 `next`  
 迭代器，定址對象是所插入字串的第一個元素。  
  
 `_Iosbase`  
 指定的資料流，其中包含帶有 numpunct facet 的地區設定，可用來為輸出和旗標加上標點符號以設定輸出格式。  
  
 `_Fill`  
 間距所使用的字元。  
  
 `val`  
 要輸出的數字或布林值類型。  
  
### <a name="return-value"></a>傳回值  
 輸出迭代器，定址對象是所產生之最後一個元素的後面一個位置。  
  
### <a name="remarks"></a>備註  
 第一個虛擬的受保護成員函式會從 `next` 開始產生一系列元素，以從 `val` 的值產生整數輸出欄位。 此函式會傳回迭代器，此迭代器指定在所產生的整數輸出欄位後下一個要插入元素的位置。  
  
 產生整數輸出欄位的規則，與列印函式在將一系列 `char` 元素產生至檔案時所使用的規則相同。 每個這類 char 元素都會被假設為與 **CharType** 類型的對等元素以簡單、一對一的對應方式對應。 不過，在列印函式使用空格或數字 0 來填補欄位的地方，`do_put` 會改用 **fill**。 對等的列印轉換規格是以下列方式決定：  
  
-   如果 **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct)，則轉換規格為 **lo**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex)，則轉換規格為 **lx**。  
  
-   否則，轉換規格會是 **ld**。  
  
 如果 **iosbase**. [width](../standard-library/ios-base-class.md#width) 不是零，就會在前面加上此值的欄位寬度。 接著，函式會呼叫 **iosbase**. **width**(0) 將欄位寬度重設為零。  
  
 只有當指定輸出欄位所需的元素數目下限 *N* 小於 **iosbase**. [width](../standard-library/ios-base-class.md#width) 時，才需要進行填補。 此類填補所組成的序列*N* - **寬度**副本**填滿**。 接著，填補會以下列方式進行：  
  
-   如果 **iosbase**. **旗標** & `ios_base::adjustfield` == `ios_base::`[左](../standard-library/ios-functions.md#left)，旗標 **-** 前面加上。 (填補的發生位置是在已產生的文字之後)。  
  
-   如果 **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal)，就會在前面加上 **0** 旗標。 (就數字輸出欄位而言，會在列印函式以 0 填補的地方進行填補)。  
  
-   否則，不會在前面加上任何額外的旗標。 (填補字元會出現在已產生的序列之前)。  
  
 最後：  
  
-   如果 **iosbase**. **flags** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) 不是零，就會在轉換規格前面加上 **+** 旗標。  
  
-   如果 **iosbase**. **flags** & **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) 不是零，就會在轉換規格前面加上 **#** 旗標。  
  
 整數輸出欄位的格式會進一步由 [locale facet](../standard-library/locale-class.md#facet_class)**fac** (由 [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 呼叫所傳回) 決定。 尤其是：  
  
- **fac**. [grouping](../standard-library/numpunct-class.md#grouping) 會決定任何小數點左邊數字分組的方式  
  
- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) 會決定任何小數點左邊分隔數字群組的序列  
  
 如果 **fac**. **grouping** (其第一個元素的值為 CHAR_MAX) 未施加任何千分號條件約束，就不會有任何 **fac**. `thousands_sep` 執行個體在輸出欄位中產生。 否則，會在進行列印轉換之後插入分隔符號。  
  
 第二個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    unsigned long val) const;
```  
  
 行為與第一個相同，不同的是，它會以 **lu** 取代 **ld** 轉換規格。  
  
 第三個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    double val) const;
```  
  
 行為與第一個相同，不同的是，它會從 **val** 的值產生浮點數輸出欄位。 **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) 會決定將整數與小數分隔的序列。 對等的列印轉換規格是以下列方式決定：  
  
-   如果 **iosbase**. **flags** & `ios_base::floatfield` == `ios_base::`[fixed](../standard-library/ios-functions.md#fixed)，則轉換規格為 **lf**。  
  
-   如果 **iosbase**. **flags** & **ios_base::floatfield** == `ios_base::`[scientific](../standard-library/ios-functions.md#scientific)，則轉換規格為 `le`。 如果 **iosbase**. **flags** & `ios_base::`[uppercase](../standard-library/ios-functions.md#uppercase) 不是零，就會以 **E** 取代 **e**。  
  
-   否則，轉換規格會是 **lg**。 如果 **iosbase**. **flags** & **ios_base::uppercase** 不是零，就會以 **G** 取代 **g**。  
  
 如果 **iosbase**. **flags** & **ios_base::fixed** 不是零，或如果 **iosbase**. [precision](../standard-library/ios-base-class.md#precision) 大於零，就會在轉換規格前面加上值為 **iosbase**. **precision** 的有效位數。 所有填補行為都與整數輸出欄位的填補行為相同。 填補字元為 **fill**。 最後：  
  
-   如果 **iosbase**. **flags** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) 不是零，就會在轉換規格前面加上 **+** 旗標。  
  
-   如果 **iosbase**. **flags** & `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) 不是零，就會在轉換規格前面加上 **#** 旗標。  
  
 第四個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    long double val) const;
```  
  
 行為與第三個相同，不同的是，轉換規格中的限定詞 **l** 會被 **L** 取代。  
  
 第五個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    const void* val) const;
```  
  
 行為與第一個相同，不同的是，轉換規格為 `p`**,** 再加上指定填補時所需的任何限定詞。  
  
 第六個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    bool val) const;
```  
  
 行為與第一個相同，不同的是，它會從 `val` 產生布林值輸出欄位。  
  
 布林值輸出欄位採用下列兩種形式其中之一。 如果 **iosbase**. **flags** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) 為 **false**，成員函式就會傳回 `do_put`(_ *Next*, \_ *Iosbase*, \_ *Fill*, ( **long**) `val`)，這通常會產生一個 0 (代表 **false**) 或 1 (代表 **true**) 的產生序列。 否則，產生的序列會是 **fac**. [falsename](../standard-library/numpunct-class.md#falsename)`)` (代表 **false**) 或 **fac**. [truename](../standard-library/numpunct-class.md#truename) (代表 **true**)。  
  
 第七個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    long long val) const;
```  
  
 行為與第一個相同，不同的是，它會以 **lld** 取代 **ld** 轉換規格。  
  
 第八個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    unsigned long long val) const;
```  
  
 行為與第一個相同，不同的是，它會以 `llu` 取代 `ld` 轉換規格。  
  
### <a name="example"></a>範例  
  請參閱 [put](#put) 的範例，它會呼叫 `do_put`。  
  
##  <a name="iter_type"></a>  num_put::iter_type  
 描述輸出迭代器的類型。  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型與範本參數 **OutputIterator** 同義。  
  
##  <a name="num_put"></a>  num_put::num_put  
 `num_put` 類型物件的建構函式。  
  
```  
explicit num_put(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>參數  
 `_Refs`  
 整數值，用來指定物件的記憶體管理類型。  
  
### <a name="remarks"></a>備註  
 `_Refs` 參數的可能值和其意義如下：  
  
-   0：物件的存留期由包含該物件的地區設定來管理。  
  
-   1：物件的存留期必須以手動方式管理。  
  
-   \>1： 未定義這些值。  
  
 無法提供任何直接範例，因為解構函式受到保護。  
  
 建構函式會以 **locale::**[facet](../standard-library/locale-class.md#facet_class)(_ *Refs*) 將其基底物件初始化。  
  
##  <a name="put"></a>  num_put::put  
 將數字轉換成 **CharType** 序列，以代表為特定地區設定格式化的數字。  
  
```  
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    bool val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    unsigned long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    Long long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    Unsigned long long val) const;

 
 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    double val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long double val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const void* val) const;
```  
  
### <a name="parameters"></a>參數  
 `dest`  
 迭代器，定址對象是所插入字串的第一個元素。  
  
 `_Iosbase`  
 指定的資料流，其中包含帶有 numpunct facet 的地區設定，可用來為輸出和旗標加上標點符號以設定輸出格式。  
  
 `_Fill`  
 間距所使用的字元。  
  
 `val`  
 要輸出的數字或布林值類型。  
  
### <a name="return-value"></a>傳回值  
 輸出迭代器，定址對象是所產生之最後一個元素的後面一個位置。  
  
### <a name="remarks"></a>備註  
 所有成員函式都會傳回 [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `val`)。  
  
### <a name="example"></a>範例  
  
```cpp  
// num_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
   basic_stringstream<char> psz2;  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << "The thousands separator is: "   
        << use_facet < numpunct <char> >(loc).thousands_sep( )   
        << endl;  
  
   psz2.imbue( loc );  
   use_facet < num_put < char > >  
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),  
                    psz2, ' ', fVal=1000.67);  
  
   if ( st & ios_base::failbit )  
      cout << "num_put( ) FAILED" << endl;  
   else  
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;  
}  
```  
  
```Output  
The thousands separator is: .  
num_put( ) = 1.000,67  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<locale>](../standard-library/locale.md)   
 [facet 類別](../standard-library/locale-class.md#facet_class)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
