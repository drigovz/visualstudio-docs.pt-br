---
title: Disponibilidade do comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838285"
---
# <a name="command-availability"></a>Disponibilidade de comando
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O contexto do Visual Studio determina quais comandos estão disponíveis. O contexto pode ser alterado dependendo do projeto atual, do editor atual, do VSPackages que são carregados e de outros aspectos do IDE (ambiente de desenvolvimento integrado).  
  
## <a name="command-contexts"></a>Contextos de comando  
 Os seguintes contextos de comando são os mais comuns.  
  
- **IDE** Os comandos fornecidos pelo IDE estão sempre disponíveis.  
  
- **VSPackage** VSPackages pode definir quando os comandos devem ser exibidos ou ocultos.  
  
- **Projeto** do Os comandos do projeto aparecem apenas para o projeto selecionado no momento.  
  
- **Editor** do Somente um editor pode estar ativo por vez. Os comandos do editor ativo estão disponíveis. Um editor trabalha em conjunto com um serviço de linguagem. O serviço de idioma deve processar seus comandos no contexto do editor associado.  
  
- **Tipo de arquivo** Um editor pode carregar mais de um tipo de arquivo. Os comandos disponíveis podem ser alterados dependendo do tipo de arquivo.  
  
- **Janela ativa** A janela do último documento ativo define o contexto da interface do usuário para associações de chave. No entanto, uma janela de ferramenta que tem uma tabela de associação de chave que se assemelha ao navegador da Web interno também pode definir o contexto da interface do usuário. Para janelas de documentos com várias guias, como o editor de HTML, cada guia tem um GUID de contexto de comando diferente. Depois que uma janela de ferramentas é registrada, ela está sempre disponível no menu **Exibir** .  
  
- **Contexto da interface do usuário** Os contextos da interface do usuário são identificados pelos valores da <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> quando a solução está sendo compilada ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> quando o depurador está ativo. Vários contextos de interface do usuário podem estar ativos ao mesmo tempo.  
  
## <a name="defining-custom-context-guids"></a>Definindo GUIDs de contexto personalizados  
 Se um GUID de contexto de comando apropriado ainda não estiver definido, você poderá definir um em seu VSPackage e, em seguida, programá-lo para estar ativo ou inativo conforme necessário para controlar a visibilidade de seus comandos.  
  
1. Registre GUIDs de contexto chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> método.  
  
2. Obtenha o estado de um GUID de contexto chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método.  
  
3. Ativar e desativar os GUIDs de contexto chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> método.  
  
    > [!CAUTION]
    > Verifique se o VSPackage não afeta nenhum GUID de contexto existente porque outros VSPackages podem depender deles.  
  
## <a name="see-also"></a>Consulte Também  
 [Objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md)   
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
