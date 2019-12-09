---
title: Associar a uma caixa&#39;de diálogo de propriedade de atividade (herdada) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 451544a84237bc6fa4e069df9dd1e17feccf86f7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301016"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Associar a uma caixa&#39;de diálogo de propriedade de atividade (herdada)
Este tópico descreve como usar a caixa de diálogo **associar a uma propriedade de uma atividade** no [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Um tipo de instância de propriedade de dependência pode ser associado a propriedade pública ou ao evento de outra atividade. Para obter mais informações sobre associação de atividade, consulte [usando propriedades de dependência](https://go.microsoft.com/fwlink?LinkID=65007).

 Você seleciona uma propriedade para associar usando a caixa de diálogo **associar a uma propriedade de uma atividade** . Você abre essa caixa de diálogo clicando nas reticências **[...]** no final da caixa de texto da propriedade selecionada na janela **Propriedades** ou clicando no ícone de ponto de exclamação azul que aparece ao lado do nome da propriedade no navegador de propriedades.

 A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **associar à propriedade de uma atividade** .

|Elemento da interface|Descrição|
|----------------|-----------------|
|**Associar a um membro existente**|Selecione um membro que você deseja associar no painel modo de exibição de árvore. O painel abaixo de exibição de árvore exibe uma mensagem que indica se o membro é um tipo válido para associar a ou não. Clique em **OK** para associar ao membro válido selecionado.|
|**Associar a um novo membro**|Crie um novo campo ou propriedade de membro para associação. Insira um **novo nome de membro**. Escolha se deseja criar uma propriedade de dependência ou um campo público selecionando **criar campo** ou **criar Propriedade**. Clique em **OK** para criar o novo membro.|

## <a name="see-also"></a>Consulte também
 [Usando propriedades de atividade](https://go.microsoft.com/fwlink?LinkID=65013) [usando propriedades de dependência](https://go.microsoft.com/fwlink?LinkID=65007) [Designer herdado para ajuda da interface do usuário Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)