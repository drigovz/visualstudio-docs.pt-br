---
title: Disponibilidade de comando | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7dfe8a6b3e4c84fd97a159f6ac43e0de47536f0b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064259"
---
# <a name="command-availability"></a>Disponibilidade do comando

O contexto do Visual Studio determina quais comandos estão disponíveis. O contexto pode mudar dependendo do projeto atual, o editor atual, os VSPackages que são carregados e outros aspectos do ambiente de desenvolvimento integrado (IDE).

## <a name="command-contexts"></a>Contextos de comando

Os contextos de comando a seguir são as mais comuns:

- IDE: Comandos fornecidos pelo IDE estão sempre disponíveis.

- {1&gt;VSPackage&lt;1}. Os VSPackages pode definir quando comandos devem ser exibidas ou ocultas.

- Projeto: Comandos de projeto aparecem somente para o projeto selecionado atualmente.

- Editor: Apenas um editor pode estar ativo por vez. Comandos do editor ativo estão disponíveis. Um editor trabalha junto com um serviço de linguagem. O serviço de linguagem deve processar seus comandos no contexto do editor associado.

- Tipo de arquivo: Um editor pode carregar mais de um tipo de arquivo. Os comandos disponíveis podem mudar dependendo do tipo de arquivo.

- Janela ativa: A última janela do documento ativo define o contexto de (UI) de interface do usuário para associações de teclas. No entanto, uma janela de ferramenta que tem uma tabela de associação de chave que se parece com o navegador da web interno também pode definir o contexto de interface do usuário. Para janelas de documento com várias guias, como o editor de HTML, cada guia tem um GUID de contexto do comando diferente. Depois que uma janela de ferramentas é registrada, ele está sempre disponível na **exibição** menu.

- Contexto de interface do usuário: Contextos de interface do usuário são identificados pelos valores da <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, por exemplo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> quando a solução está sendo criada, ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> quando o depurador está ativo. Vários contextos de interface do usuário podem estar ativos ao mesmo tempo.

## <a name="define-custom-context-guids"></a>Definir contexto personalizado GUIDs

Se um contexto de comando apropriado que GUID já não está definido, poderá definir um em seu VSPackage e, em seguida, programá-lo para ser ativos ou inativos conforme necessário para controlar a visibilidade de seus comandos:

1. Registre os GUIDs de contexto chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> método.

2. Obter o estado de um GUID de contexto chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> método.

3. Ativar e desativar os GUIDs de contexto chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> método.

> [!CAUTION]
> Certifique-se de que o VSPackage não afeta nenhum contexto existente GUIDs porque pode depender de outros VSPackages neles.

## <a name="see-also"></a>Consulte também

- [Objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md)
- [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)