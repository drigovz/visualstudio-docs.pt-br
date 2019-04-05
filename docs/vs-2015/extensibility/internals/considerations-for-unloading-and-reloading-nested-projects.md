---
title: Considerações para descarregar e recarregar projetos de aninhados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929560"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerações para descarregar e recarregar projetos aninhados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando você implementa os tipos de projeto aninhado, você deve executar etapas adicionais quando você descarrega e recarregar os projetos. Para notificar os ouvintes de eventos de solução corretamente, você deverá gerar corretamente os `OnBeforeUnloadProject` e `OnAfterLoadProject` eventos.  
  
 Um motivo que você deve criar esses eventos dessa maneira é que você não deseja que o controle do código fonte (SCC) para excluir os itens do servidor e, em seguida, adicioná-los de volta como algo novo se não houver um `Get` operação do SCC. Nesse caso, um novo arquivo seria carregado fora de SCC e você tem que descarregar e recarregar todos os arquivos, caso sejam diferentes. Chamadas de SCC `ReloadItem`. A implementação dessa chamada é excluir o projeto e recriá-la novamente com a implementação `IVsFireSolutionEvents` chamar `OnBeforeUnloadProject` e `OnAfterLoadProject`. Quando você executa essa implementação, o SCC é informado de que o projeto foi excluído e adicionado novamente temporariamente. Portanto, o SCC não funcionará no projeto como se o projeto foi realmente excluído do servidor e, em seguida, adicionado novamente.  
  
## <a name="reloading-projects"></a>Recarregar projetos  
 Para dar suporte a recarregamento de projetos aninhados, você deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. Em sua implementação de `ReloadItem`, feche os projetos aninhados e, em seguida, recriá-los.  
  
 Normalmente quando um projeto é recarregado, o IDE gera o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> e o `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` eventos. No entanto, para projetos aninhados que serão excluídos e recarregados, o projeto pai inicia o processo, não do IDE. Como o projeto pai não gera eventos de solução, e o IDE não possui informações sobre a inicialização do processo, os eventos não são gerados.  
  
 Para lidar com esse processo, as chamadas de projeto pai `QueryInterface` sobre o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> fora da interface a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interface. `IVsFireSolutionEvents` tem funções que mandar o IDE para gerar o `OnBeforeUnloadProject` evento para descarregar o projeto aninhado e, em seguida, gerar o `OnAfterLoadProject` evento para recarregar o projeto mesmo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Aninhar projetos](../../extensibility/internals/nesting-projects.md)
