---
title: Aplicativo de configurações em várias conexões de projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203854"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicação de configurações em várias conexões de projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um plug-in de controle do código-fonte criado usando a API de plug-in de controle do código-fonte 1,2 pode usar uma operação em lote para executar a mesma operação de controle do código-fonte em vários projetos ou em vários contextos de conexão. Os lotes podem ser usados para eliminar caixas de diálogo redundantes por projeto da experiência do usuário.  
  
 Se um usuário selecionar vários itens que pertencem a mais de uma conexão em um plug-in de controle do código-fonte criado usando a API de plug-in de controle do código-fonte 1,1 (por exemplo, dois projetos da Web em diferentes máquinas de compartilhamento de arquivos) e os verificar, o usuário verá a mesma caixa de diálogo repetidamente. Isso acontece mesmo que o usuário clique na caixa de seleção **aplicar a todos** na caixa de diálogo, pois o IDE redefine seu estado para cada contexto de conexão.  
  
## <a name="new-capability-flag"></a>Novo sinalizador de funcionalidade  
 `SccBeginBatch` A função define o `SCC_CAP_BATCH` sinalizador para indicar que uma operação em lote está em andamento  
  
## <a name="new-functions"></a>Novas funções  
 As novas funções a seguir dão suporte à operação em lote:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  A `SCCBeginBatch` função inicia um grupo de operações de controle do código-fonte. `SccEndBatch` Fecha o grupo. Os grupos não podem ser aninhados.  
  
## <a name="see-also"></a>Consulte Também  
 [Novidades na API do plug-in de controle do código-fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
