---
title: Comparar pasta do projeto ao repositório de controle do código-fonte | Microsoft Docs
description: Na API de plug-in de controle do código-fonte, a comparação entre a pasta do projeto local e o controle do código-fonte é realizada usando SccDirQueryInfo e SccDirDiff.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed69c6e503614cd1b2ed8e21716a5edcb4babd2b
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877579"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparação opcional da pasta do projeto local para o repositório de controle do código-fonte
Na API de plug-in de controle do código-fonte 1,2 a comparação entre a pasta do projeto local e o controle do código-fonte é realizada usando as funções [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 Em **Gerenciador de soluções**, se uma pasta for selecionada em vez de um arquivo individual, o menu de atalho **comparar versões** invocará o novo [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md) no plug-in de controle do código-fonte.

## <a name="new-capability-flags"></a>Novos sinalizadores de capacidade
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Novas funções
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 A `SccDirQueryInfo` função é chamada antes `SccDirDiff` para determinar se o diretório de trabalho é controlado por origem. A `SccDirDiff` função exibe as diferenças entre o diretório local atual e a pasta de controle do código-fonte correspondente. Esse comando solicita que o plug-in de controle do código-fonte exiba a lista de alterações no diretório. Um plug-in de controle do código-fonte fornece sua própria interface do usuário para exibir as diferenças.

> [!NOTE]
> Essa função usa os mesmos sinalizadores de comando que [SccDiff](../../extensibility/sccdiff-function.md). Como um provedor de plug-in de controle do código-fonte, você pode optar por não dar suporte à operação de "diferença rápida" para diretórios.

## <a name="see-also"></a>Consulte também
- [Novidades na API do plug-in de controle do código-fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
