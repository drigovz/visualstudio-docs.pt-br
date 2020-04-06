---
title: Compare a pasta do projeto com a Loja de Controle de Origem | Microsoft Docs
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
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706858"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparação opcional da pasta do projeto local para o repositório de controle do código-fonte
No controle de origem A API 1.2, a comparação entre a pasta de projeto local e o controle de origem é realizada usando as funções [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 No **Solution Explorer**, se uma pasta for selecionada em vez de um arquivo individual, o menu de atalho Compare **versões** invoca os novos [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md) no plug-in de controle de origem.

## <a name="new-capability-flags"></a>Novas bandeiras de capacidade
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Novas funções
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 A `SccDirQueryInfo` função é `SccDirDiff` chamada antes para determinar se o diretório de trabalho é controlado pela fonte. A `SccDirDiff` função exibe as diferenças entre o diretório local atual e a pasta de controle de origem correspondente. Este comando pede que o plug-in de controle de origem exiba a lista de alterações no diretório. Um plug-in de controle de origem fornece sua própria ui para exibir as diferenças.

> [!NOTE]
> Esta função usa os mesmos sinalizadores de comando [do SccDiff](../../extensibility/sccdiff-function.md). Como um provedor de plug-in de controle de origem, você pode optar por não suportar a operação "quick diff" para diretórios.

## <a name="see-also"></a>Confira também
- [Novidades na API do plug-in de controle do código-fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
