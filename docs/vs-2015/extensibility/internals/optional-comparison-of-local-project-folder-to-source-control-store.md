---
title: Comparação opcional da pasta de projeto Local para a Store de controle do código-fonte | Microsoft Docs
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
ms.openlocfilehash: 34b9a7ff7d4cc70863090957060db90edfd016b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923896"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparação opcional da pasta do projeto local para o repositório de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

No código-fonte 1.2 de API de plug-in a comparação entre a pasta do projeto local e o controle de origem é realizada usando as funções de controle [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 Dentro de **Gerenciador de soluções**, se uma pasta está selecionada, em vez de um arquivo individual, o **comparar versões** menu de atalho invoca o novo [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [ SccDirDiff](../../extensibility/sccdirdiff-function.md) no plug-in de controle de origem.  
  
## <a name="new-capability-flags"></a>Novos sinalizadores de recurso  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Novas funções  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 O `SccDirQueryInfo` função é chamada antes de `SccDirDiff` para determinar se o diretório de trabalho é o controle do código-fonte. O `SccDirDiff` função exibe as diferenças entre o diretório local atual e a pasta de controle do código-fonte correspondente. Esse comando solicita que o plug-in para exibir a lista de alterações para o diretório de controle de origem. Um plug-in de controle do código-fonte fornece sua própria interface do usuário para exibir as diferenças.  
  
> [!NOTE]
>  Essa função usa os mesmos sinalizadores de comando como [SccDiff](../../extensibility/sccdiff-function.md). Como um provedor de plug-in de controle de origem, você pode optar por não oferece suporte à operação "diff rápido" para diretórios.  
  
## <a name="see-also"></a>Consulte também  
 [Novidades na Versão 1.2 da API do plug-in de controle de código-fonte](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
