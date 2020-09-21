---
title: Comparação opcional da pasta do projeto local para o repositório de controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be26b4195e0db7b3b78fcc2223ff2a6f8bde47d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838598"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparação opcional da pasta do projeto local para o repositório de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Na API de plug-in de controle do código-fonte 1,2 a comparação entre a pasta do projeto local e o controle do código-fonte é realizada usando as funções [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 Em **Gerenciador de soluções**, se uma pasta for selecionada em vez de um arquivo individual, o menu de atalho **comparar versões** invocará o novo [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md) no plug-in de controle do código-fonte.  
  
## <a name="new-capability-flags"></a>Novos sinalizadores de capacidade  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Novas funções  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 A `SccDirQueryInfo` função é chamada antes `SccDirDiff` para determinar se o diretório de trabalho é controlado por origem. A `SccDirDiff` função exibe as diferenças entre o diretório local atual e a pasta de controle do código-fonte correspondente. Esse comando solicita que o plug-in de controle do código-fonte exiba a lista de alterações no diretório. Um plug-in de controle do código-fonte fornece sua própria interface do usuário para exibir as diferenças.  
  
> [!NOTE]
> Essa função usa os mesmos sinalizadores de comando que [SccDiff](../../extensibility/sccdiff-function.md). Como um provedor de plug-in de controle do código-fonte, você pode optar por não dar suporte à operação de "diferença rápida" para diretórios.  
  
## <a name="see-also"></a>Consulte Também  
 [Novidades na API do plug-in de controle do código-fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
