---
title: Enumerador de código de status de diretório | Microsoft Docs
description: O enumerador SccDirStatus contém valores constantes nomeados que especificam o estado de um diretório no sistema de controle do código-fonte e são usados pelo SccDirQueryInfo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6d5eb64cf4883c2e977b41e77fc2243aca2ee34
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968249"
---
# <a name="directory-status-code-enumerator"></a>Enumerador de código de status de diretório
O `SccDirStatus` enumerador contém valores constantes nomeados que especificam o estado de um diretório no sistema de controle do código-fonte. Essa enumeração é usada pelo [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Isso foi introduzido na versão 1,2 da API de plug-in de controle do código-fonte.

## <a name="syntax"></a>Sintaxe

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Membros
 Não foi possível obter SCC_DIRSTATUS_INVALID status; Não confie nela.

 SCC_DIRSTATUS_NOTCONTROLLED diretório não está no controle do código-fonte.

 SCC_DIRSTATUS_CONTROLLED diretório está sob controle do código-fonte.

 SCC_DIRSTATUS_EMPTYPROJ projeto correspondente a esse diretório está vazio.

## <a name="see-also"></a>Consulte também
- [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
