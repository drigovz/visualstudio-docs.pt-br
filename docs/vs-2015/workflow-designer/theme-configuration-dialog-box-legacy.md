---
title: Caixa de diálogo configuração de tema (herdada) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ThemeConfigurationDialog.UI
helpviewer_keywords:
- themes, configuring
- Theme Configuration dialog box
ms.assetid: 9e6d182a-c4d9-4e71-b2b9-02f675fc2b29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8171c6dcfe285ade07531896893915d0e209e0c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670188"
---
# <a name="theme-configuration-dialog-box-legacy"></a>Caixa de diálogo de configuração tema (legados)
Este tópico descreve como usar a caixa de diálogo **configuração de tema** no [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Um tema define o plano de fundo e de primeiro plano as cores, estilos, ícones, e outros elementos visuais de um fluxo de trabalho. Você pode salvar temas para reutilização por outros fluxos de trabalho.

 Você cria e edita temas usando a caixa de diálogo **configuração de tema** . Para abrir a caixa de diálogo, selecione **criar novo tema** no menu **fluxo de trabalho** ou clique com o botão direito do mouse na superfície de design do fluxo de trabalho e selecione **criar novo tema**.

 A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **configuração de tema** .

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Nome do tema:**|O nome que identifica o tema na [caixa de diálogo temas, designer de fluxo de trabalho, opções (Herdado)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md). Um nome de variável é gerado para novos temas.|
|**Local do tema:**|Nome de arquivo e caminho do arquivo de tema. Um nome de arquivo variável é gerado para novos temas gerado com base no nome do tema. Se você alterar o nome gerado de tema, convém alterar o nome de arquivo para corresponder ao nome do tema.|
|**...**|Clique para selecionar o local para salvar o arquivo de tema de fluxo de trabalho, que usa uma extensão de nome de arquivo .wtm. O caminho selecionado será visto na caixa de texto **local do tema** .|
|**Selecione designer e configure Propriedades:**|O painel esquerdo lista um modo de exibição de árvore de atividades para que o tema pode ser personalizado. Selecione uma atividade no modo de exibição de árvore e propriedades de tema para atividades serão exibidas no painel de propriedades, que é à direita do painel modo de exibição de árvore. Clique em uma propriedade para alterar seu valor.|
|**Visualizar**|Clique para exibir uma janela para visualizar os efeitos de alterações de propriedade.|

## <a name="see-also"></a>Consulte também
 [Caixa de diálogo temas, designer de fluxo de trabalho, opções (Herdado)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md) [Designer herdado para ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)