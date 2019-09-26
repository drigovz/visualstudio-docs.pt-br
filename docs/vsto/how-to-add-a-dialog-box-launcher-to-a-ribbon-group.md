---
title: 'Como: Adicionar um iniciador de caixa de diálogo a um grupo de faixa de faixas'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b930348845e04dca089cf153a11cc2a9fd29c880
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255899"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Como: Adicionar um iniciador de caixa de diálogo a um grupo de faixa de faixas
  Você pode adicionar um iniciador de caixa de diálogo a qualquer grupo em uma faixa de faixas. Um iniciador de caixa de diálogo é um pequeno ícone que aparece em um grupo. Os usuários clicam nesse ícone para abrir caixas de diálogo ou painéis de tarefas relacionados que fornecem mais opções relacionadas ao grupo.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Para adicionar um iniciador de caixa de diálogo a um grupo de faixa de faixas

1. Selecione o arquivo de código da faixa de opções (arquivo *. vb* ou *. cs* ) em **Gerenciador de soluções**.

2. No menu **Exibir** , clique em **Designer**.

3. No designer de faixa de faixas, clique com o botão direito do mouse em qualquer grupo e clique em **Adicionar DialogBoxLauncher**.

     Adicione código ao <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> evento do grupo para abrir uma caixa de diálogo personalizada ou interna.

## <a name="see-also"></a>Consulte também
- [Visão geral da faixa de faixas](../vsto/ribbon-overview.md)
- [Acessar a faixa de faixas em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Designer de faixa de das](../vsto/ribbon-designer.md)
- [Visão geral do modelo de objeto Ribbon](../vsto/ribbon-object-model-overview.md)
- [XML da faixa de opções](../vsto/ribbon-xml.md)
- [Como: Exportar uma faixa de faixas do designer de faixa de das para XML da faixa de das](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Como: Alterar a posição de uma guia na faixa de posições](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Como: Personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md)
- [Como: Adicionar controles ao modo de exibição de Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Personalizar uma faixa de faixas para o Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Como: Introdução à personalização da faixa de faixas](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Como: Mostrar erros da interface do usuário do suplemento](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Passo a passo: Criar uma guia personalizada usando o designer de faixa de faixas](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Passo a passo: Atualizar os controles em uma faixa de faixas em tempo de execução](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Passo a passo: Criar uma guia personalizada usando o XML da faixa de uma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
