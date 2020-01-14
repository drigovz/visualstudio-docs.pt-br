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
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849330"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Como: Crie uma condição declarativa de regra (o legados)
Este tópico descreve como declarar uma condição de regra usando o novas [!INCLUDE[wfd1](../includes/wfd1-md.md)] que direciona [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Uma instrução Condition é avaliada como **true** ou **false**. Uma condição de regra declarativa é uma instrução de condição criada usando a [caixa de diálogo Editor de condição de regra (herdada)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e armazenada como XML com o fluxo de trabalho. Pode incluir os predicados que comparam o estado de fluxo de trabalho e a algebra booleano que combina vários predicados.

 As condições declarativas de regras são usadas nas seguintes atividades de para fora da caixa do Windows Workflow Foundation:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Para criar uma condição de regra declarativamente usando o editor de condição de regra

1. Na janela **Propriedades** da atividade, clique na propriedade **condição** ou na propriedade **UntilCondition** , dependendo da atividade.

2. Selecione **condição de regra declarativa** na lista para a propriedade.

3. Expanda a propriedade **Condition** ou **UntilCondition** .

4. Clique na propriedade **ConditionName** .

5. Clique nas reticências **condicionaname** **[...]** para abrir a caixa de diálogo **Selecionar condição** .

6. Clique em **nova condição** para abrir a caixa de diálogo **Editor de condição de regra** .

7. Digite a expressão da condição na caixa de texto **condição** .

     Para obter informações sobre como criar expressões de condição, consulte [caixa de diálogo Editor de condição de regra (Herdado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Quando terminar de criar a expressão de condição, clique em **OK** para fechar a caixa de diálogo e criar a condição de regra com um nome atribuído.

     A caixa de diálogo **Selecionar condição** é aberta.

     Para obter informações sobre como usar a caixa de diálogo **Selecionar condição** , consulte [caixa de diálogo Selecionar condição (herdada)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Veja também
 [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md) [usando o ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx) [usando a atividade IfElseBranchActivity](https://msdn2.microsoft.com/library/bb628465.aspx) [usando a atividade de replicador](https://msdn2.microsoft.com/library/bb628544.aspx) [usando a caixa de diálogo do editor de condição de atividade While](https://msdn2.microsoft.com/library/bb628552.aspx) [(Herdado)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [caixa de diálogo de seleção de condição (herdada)](../workflow-designer/select-condition-dialog-box-legacy.md) [usando condições em fluxos de trabalho](https://msdn2.microsoft.com/library/bb628447.aspx)
