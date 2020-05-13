---
title: Enumerador de código de comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15916d26ac0120417205af0bb9117a45ec0397c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739790"
---
# <a name="command-code-enumerator"></a>Enumerador de código de comando
Este enumerador é usado nas opções para o [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e o [SccPopulateList](../extensibility/sccpopulatelist-function.md)para indicar o comando para o qual as opções são especificadas.

## <a name="syntax"></a>Sintaxe

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Membros
SCC_COMMAND_GET Corresponde ao [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT Corresponde ao [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN Corresponde ao [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT Corresponde ao [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD Corresponde ao [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE Corresponde ao [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF Corresponde ao [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY Corresponde ao [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME Corresponde ao [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES Corresponde ao [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS Corresponde à [opção SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Confira também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
