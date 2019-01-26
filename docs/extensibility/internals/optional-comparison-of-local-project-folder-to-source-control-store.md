---
title: Comparar pasta do projeto para Store de controle do código-fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01ccbc50f9b88d2263f4fca913b78921ce88a4a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922149"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparação opcional da pasta do projeto local para o repositório de controle do código-fonte
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