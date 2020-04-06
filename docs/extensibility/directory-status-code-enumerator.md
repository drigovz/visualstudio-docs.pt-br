---
title: Enumerador de código de status do diretório | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b5ebf61f2baa6e4277e27cd3c4d18a51e64f835
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712153"
---
# <a name="directory-status-code-enumerator"></a>Enumerador de código de status do diretório
O `SccDirStatus` enumerador contém valores constantes nomeados que especificam o estado de um diretório no sistema de controle de origem. Esta enumeração é usada pelo [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Isso foi introduzido na versão 1.2 da API plug-in de controle de origem.

## <a name="syntax"></a>Sintaxe

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Membros
 SCC_DIRSTATUS_INVALID status não pôde ser obtido; não confie nisso.

 SCC_DIRSTATUS_NOTCONTROLLED Diretório não está sob controle de origem.

 SCC_DIRSTATUS_CONTROLLED diretório está sob controle de origem.

 SCC_DIRSTATUS_EMPTYPROJ Projeto correspondente a este diretório está vazio.

## <a name="see-also"></a>Confira também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
