---
title: Disponibilidade de comando | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709694"
---
# <a name="command-availability"></a>Disponibilidade de comando

O contexto do Visual Studio determina quais comandos estão disponíveis. O contexto pode mudar dependendo do projeto atual, do editor atual, dos VSPackages carregados e de outros aspectos do ambiente de desenvolvimento integrado (IDE).

## <a name="command-contexts"></a>Contextos de comando

Os seguintes contextos de comando são os mais comuns:

- IDE: Os comandos fornecidos pelo IDE estão sempre disponíveis.

- VSPackage: VSPacotes podem definir quando os comandos devem ser exibidos ou ocultos.

- Projeto: Os comandos do projeto aparecem apenas para o projeto selecionado no momento.

- Editor: Apenas um editor pode estar ativo por vez. Os comandos do editor ativo estão disponíveis. Um editor trabalha em estreita colaboração com um serviço de idiomas. O serviço de idiomas deve processar seus comandos no contexto do editor associado.

- Tipo de arquivo: Um editor pode carregar mais de um tipo de arquivo. Os comandos disponíveis podem ser trocados dependendo do tipo de arquivo.

- Janela ativa: A última janela de documento ativo define o contexto da interface do usuário (UI) para vinculações de chaves. No entanto, uma janela de ferramenta que tenha uma tabela de vinculação de tecla que se assemelha ao navegador interno da Web também poderia definir o contexto de Interface do Usuário. Para janelas de documentos com várias guias, como o editor HTML, cada guia tem um guid de contexto de comando diferente. Depois que uma janela de ferramenta é registrada, ela está sempre disponível no menu **Exibir.**

- Contexto de Interface do Usuário: Os contextos <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> de Interface <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> do Usuário são identificados <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> pelos valores da classe, por exemplo, quando a solução está sendo construída ou quando o depurador está ativo. Vários contextos de interface do reino do reino eletrônico podem estar ativos ao mesmo tempo.

## <a name="define-custom-context-guids"></a>Defina GUIDs de contexto personalizado

Se um GUID de contexto de comando apropriado ainda não estiver definido, você pode definir um em seu VSPackage e, em seguida, programá-lo para ser ativo ou inativo, conforme necessário para controlar a visibilidade de seus comandos:

1. Registre GUIDs de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> contexto chamando o método.

2. Obtenha o estado de um <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> GUID de contexto chamando o método.

3. Ligue e desligue os GUIDs <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> de contexto chamando o método.

> [!CAUTION]
> Certifique-se de que o vsPackage não afete nenhum GUIDs de contexto existente porque outros VSPackages podem depender deles.

## <a name="see-also"></a>Confira também

- [Objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md)
- [Como o VSPackages adiciona elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
