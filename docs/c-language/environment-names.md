---
title: 環境名稱
ms.date: 11/04/2016
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
ms.openlocfilehash: 67c49c256945eb60b10b9bc19b0dca8ba0b73a84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516970"
---
# <a name="environment-names"></a>環境名稱

**ANSI 4.10.4.4**：[getenv](../c-runtime-library/reference/getenv-wgetenv.md) 函式所使用的一組環境名稱和用於修改環境清單的方法

這組環境名稱並無限制。

若要從 C 程式內部變更環境變數，請呼叫 [_putenv](../c-runtime-library/reference/putenv-wputenv.md) 函式。 若要從 Windows 的命令列變更環境變數，請使用 SET 命令 (例如 SET LIB = D:\ LIBS)。

在 C 程式內設定的環境變數只有在其作業系統命令殼層 (CMD.EXE 或 COMMAND.COM) 的主機複本執行時才存在。 例如，下面這行

```
system( SET LIB = D:\LIBS );
```

會執行命令殼層 (CMD.EXE) 的複本、設定環境變數 LIB，並返回 C 程式結束 CMD.EXE 的次要複本。 結束 CMD.EXE 的該複本會移除暫存環境變數 LIB。

同樣地，`_putenv` 函式所做的變更只會保留到程式結束為止。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)<br/>
[_putenv、_wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[getenv、_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)