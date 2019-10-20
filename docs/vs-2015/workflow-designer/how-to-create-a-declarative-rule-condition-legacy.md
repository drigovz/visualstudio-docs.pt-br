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
ms.openlocfilehash: d3a15aad987e46edb58da3560828c70571df2227
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663411"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Como: Crie uma condição declarativa de regra (o legados)
Este tópico descreve como declarar uma condição de regra usando o novas [!INCLUDE[wfd1](../includes/wfd1-md.md)] que direciona [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Uma instrução Condition é avaliada como **true** ou **false**. Uma condição de regra declarativa é uma instrução de condição criada usando a [caixa de diálogo Editor de condição de regra (herdada)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e armazenada como XML com o fluxo de trabalho. Pode incluir os predicados que comparam o estado de fluxo de trabalho e a algebra booleano que combina vários predicados.

 As condições declarativas de regras são usadas nas seguintes atividades de para fora da caixa do Windows Workflow Foundation:

- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

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

## <a name="see-also"></a>Consulte também
 [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md) [usando o ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066) [usando a atividade IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075) [usando a atividade do replicador](http://go.microsoft.com/fwlink?LinkID=65080) [usando a caixa de diálogo Editor de condição de regra de atividade While](http://go.microsoft.com/fwlink?LinkID=65091) [(herdada) ](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [Caixa de diálogo Selecionar condição (herdada)](../workflow-designer/select-condition-dialog-box-legacy.md) [usando condições em fluxos de trabalho](http://go.microsoft.com/fwlink?LinkID=65009)