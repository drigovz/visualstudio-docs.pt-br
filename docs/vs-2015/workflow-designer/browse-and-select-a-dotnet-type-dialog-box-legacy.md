---
title: Procurar e selecionar uma caixa de diálogo de tipo .NET (herdada) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e5045a62d0a654af968d50e0c309bcf8104b5cc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668980"
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Procurar e selecione uma caixa de diálogo de tipo do .NET (legados)
Este tópico descreve como usar a caixa de diálogo **procurar e selecionar um tipo .net** no [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Na janela **Propriedades** , quando você seleciona as propriedades que usam um .NET Framework tipo em um assembly referenciado, uma elipse **[...]** é exibida no final da caixa de texto da propriedade. Clicar em **[...]** abre a caixa de diálogo **procurar e selecionar um tipo .net** . Na caixa de diálogo, você pode escolher um tipo de um modo de exibição de árvore assemblies referenciados. Por exemplo, quando você estiver usando o designer de atividade, na janela **Propriedades** , clique nas reticências da **classe base** **[...]** para selecionar outra classe base para uma atividade da árvore assemblies referenciados.

 A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **procurar e selecionar um tipo do .net** .

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Nome do tipo:**|O nome do tipo selecionado.|
|**Tipo**|O painel esquerdo exibe um modo de exibição de árvore assemblies referenciados. O painel direito exibe os tipos disponíveis para a seleção do assembly referenciado selecionado no painel esquerdo.|

## <a name="see-also"></a>Consulte também
 [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)