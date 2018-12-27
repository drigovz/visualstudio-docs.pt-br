---
title: 'Como: Adicionar um iniciador da caixa de diálogo a um grupo de faixa de opções'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f6ec94b8fc170f195b00a6c093605860c97048ed
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648691"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Como: Adicionar um iniciador da caixa de diálogo a um grupo de faixa de opções
  Você pode adicionar um iniciador da caixa de diálogo a qualquer grupo de uma faixa de opções. Um iniciador da caixa de diálogo é um pequeno ícone que aparece em um grupo. Os usuários clicam nesse ícone para abrir caixas de diálogo relacionadas ou painéis de tarefas que fornecem mais opções relacionadas ao grupo.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Para adicionar um iniciador da caixa de diálogo a um grupo de faixa de opções  
  
1.  Selecione o arquivo de código da faixa de opções (*. vb* ou *. CS* arquivo) em **Gerenciador de soluções**.  
  
2.  Sobre o **modo de exibição** menu, clique em **Designer**.  
  
3.  No Designer de faixa de opções, nenhum grupo com o botão direito e, em seguida, clique em **adicionar DialogBoxLauncher**.  
  
     Adicione código para o <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> evento do grupo para abrir uma caixa de diálogo personalizada ou interna.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Acesso a faixa de opções em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Instruções passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Designer de faixa de opções](../vsto/ribbon-designer.md)   
 [Visão geral do modelo de objeto da faixa de opções](../vsto/ribbon-object-model-overview.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)   
 [Como: Exportar uma faixa de opções do Designer de faixa de opções para XML da faixa de opções](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Como: Alterar a posição de uma guia na faixa de opções](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Como: Personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md)   
 [Como: Adicionar controles ao modo de exibição backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Personalizar uma faixa de opções do Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Como: Introdução à personalização da faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Como: Mostrar erros de interface de usuário do suplemento](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Passo a passo: Criar uma guia personalizada usando o Designer de faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Passo a passo: Atualizar os controles em uma faixa de opções em tempo de execução](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Passo a passo: Criar uma guia personalizada usando o XML da faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  