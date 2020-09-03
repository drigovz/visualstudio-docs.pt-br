---
title: Considerações para descarregar e recarregar projetos aninhados | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197008"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>Considerações para descarregar e recarregar projetos aninhados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ao implementar tipos de projeto aninhados, você deve executar etapas adicionais ao descarregar e recarregar os projetos. Para notificar corretamente os ouvintes aos eventos da solução, você deve gerar corretamente os `OnBeforeUnloadProject` `OnAfterLoadProject` eventos e.  
  
 Um motivo pelo qual você deve gerar esses eventos é que você não deseja que o SCC (controle do código-fonte) exclua os itens do servidor e os adicione de volta como algo novo se houver uma `Get` operação do SCC. Nesse caso, um novo arquivo será carregado do SCC e você precisará descarregar e recarregar todos os arquivos caso eles sejam diferentes. Chamadas SCC `ReloadItem` . Sua implementação da chamada é excluir o projeto e recriá-lo novamente implementando `IVsFireSolutionEvents` para chamar `OnBeforeUnloadProject` e `OnAfterLoadProject` . Quando você executa essa implementação, o SCC é informado de que o projeto foi excluído temporariamente e adicionado novamente. Portanto, o SCC não funciona no projeto como se o projeto fosse realmente excluído do servidor e, em seguida, adicionado novamente.  
  
## <a name="reloading-projects"></a>Recarregando projetos  
 Para dar suporte ao recarregamento de projetos aninhados, você implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> método. Na implementação do `ReloadItem` , você fecha os projetos aninhados e os recria.  
  
 Normalmente, quando um projeto é recarregado, o IDE gera os <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> eventos e `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` . No entanto, para projetos aninhados que serão excluídos e recarregados, o projeto pai inicia o processo, não o IDE. Como o projeto pai não gera eventos de solução e o IDE não tem informações sobre a inicialização do processo, os eventos não são gerados.  
  
 Para lidar com esse processo, o projeto pai chama a interface para `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> fora da <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> interface. `IVsFireSolutionEvents` tem funções que instruem o IDE a gerar o `OnBeforeUnloadProject` evento para descarregar o projeto aninhado e, em seguida, gerar o `OnAfterLoadProject` evento para recarregar o mesmo projeto.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Aninhando projetos](../../extensibility/internals/nesting-projects.md)
