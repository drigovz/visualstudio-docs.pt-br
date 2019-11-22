---
title: 'Como: criar uma condição de regra declarativa (herdada) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2dc63fc58b22792e566df91bd86cac40e3fd2e65
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297487"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Como: Crie uma condição declarativa de regra (o legados)
Este tópico descreve como declarar uma condição de regra usando o novas [!INCLUDE[wfd1](../includes/wfd1-md.md)] que direciona [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Uma instrução Condition é avaliada como **true** ou **false**. Uma condição de regra declarativa é uma instrução de condição criada usando a [caixa de diálogo Editor de condição de regra (herdada)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e armazenada como XML com o fluxo de trabalho. Pode incluir os predicados que comparam o estado de fluxo de trabalho e a algebra booleano que combina vários predicados.

 As condições declarativas de regras são usadas nas seguintes atividades de para fora da caixa do Windows Workflow Foundation:

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Para criar uma condição de regra declarativamente usando o editor de condição de regra

1. Na janela de **Propriedades** de atividade, clique na propriedade de **Condição** ou propriedade de **UntilCondition** , dependendo da atividade.

2. {1&gt;Condição de Regra Declarativa&lt;1} A partir da lista para a propriedade.

3. Expanda a propriedade de **Condição** ou de **UntilCondition** .

4. Clique na propriedade de **ConditionName** .

5. Clique nas reticências **[…]** de **ConditionName** para abrir a caixa de diálogo **Selecionar Condição**.

6. Clique **Nova condição** para abrir a caixa de diálogo **Editor de Condição de Regra** .

7. Digite a expressão para a condição na caixa de texto **Condição** .

     Para obter informações sobre como criar expressões de condição, consulte [caixa de diálogo Editor de condição de regra (Herdado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Quando você terminou de criar a expressão de condição, clique **OK** para fechar a caixa de diálogo e criar a condição de regra com um nome atribuído.

     A caixa de diálogo **Selecionar Condição** abre.

     Para obter informações sobre como usar a caixa de diálogo **Selecionar condição** , consulte [caixa de diálogo Selecionar condição (herdada)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Consulte também
 [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md) [usando o ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066) [usando a atividade IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65075) [usando a atividade de replicador](https://go.microsoft.com/fwlink?LinkID=65080) [usando a caixa de diálogo do editor de condição de atividade While](https://go.microsoft.com/fwlink?LinkID=65091) [(Herdado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [caixa de diálogo de seleção de condição (herdada)](../workflow-designer/select-condition-dialog-box-legacy.md) [usando condições em fluxos de trabalho](https://go.microsoft.com/fwlink?LinkID=65009)