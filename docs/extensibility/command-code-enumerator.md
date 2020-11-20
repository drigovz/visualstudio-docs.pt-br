---
title: Enumerador de código de comando | Microsoft Docs
description: O enumerador de código de comando é usado em opções para SccGetCommandOptions e SccPopulateListto para indicar o comando para o qual as opções são especificadas.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9a831813bb975819e9152dfab4d4eefd6b440606
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974255"
---
# <a name="command-code-enumerator"></a>Enumerador de código de comando
Esse enumerador é usado nas opções de [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md)para indicar o comando para o qual as opções são especificadas.

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
SCC_COMMAND_GET corresponde ao [SccGet](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT corresponde ao [SccCheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN corresponde ao [SccCheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT corresponde ao [SccUncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD corresponde ao [SccAdd](../extensibility/sccadd-function.md).

SCC_COMMAND_REMOVE corresponde ao [SccRemove](../extensibility/sccremove-function.md).

SCC_COMMAND_DIFF corresponde ao [SccDiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY corresponde ao [SccHistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME corresponde ao [SccRename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES corresponde ao [SccProperties](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS corresponde ao [SccSetOption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Veja também
- [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
