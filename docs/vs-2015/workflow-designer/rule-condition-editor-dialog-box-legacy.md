---
title: Caixa de diálogo Editor de condição de regra (herdada) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a632b90e89e58c26ec72083fe3f4ed9223826dae
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302851"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Regra a caixa de diálogo editor de condição (o legados)
Este tópico descreve como usar a caixa de diálogo **Editor de condição de regra** no [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Você cria e modifica condições declarativas de regra usando a caixa de diálogo **Editor de condição de regra** . Essas condições de regras são expostas como propriedades nas seguintes atividades de para fora da caixa do Windows Workflow Foundation:

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

  Você acessa a caixa de diálogo **Editor de condição de regra** usando a caixa de [diálogo Selecionar condição (herdada)](../workflow-designer/select-condition-dialog-box-legacy.md).

  A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **Editor de condição de regra** .

|Elemento da interface|Descrição|
|----------------|-----------------|
|**Problema**|Insira a expressão para a condição de regra.|
|**Okey**|Clique para salvar a condição de regra.|

## <a name="entering-condition-expressions"></a>Inserindo expressões de condição
 Expressões de condição estão inseridos como texto. Você pode digitar **isso.** no editor para fazer referência a campos, propriedades e métodos usados no fluxo de trabalho, usando um menu semelhante ao IntelliSense. Ou você pode digitar um nome de membro de fluxo de trabalho diretamente. Você pode adicionar operadores lógicos a condição, como AND, OU, e NOT. Você também pode adicionar predicados. Um predicado é um operador binário e dois operandos. Os operadores binários com suporte são **==** , **>** , **\<** , **>=** e **<=** . Os operandos são suportados valor constante, função aritmética, e membros públicos o escopo.

 Você pode especificar o tipo para a comparação e pode comparar com uma cadeia de caracteres **nula** ou vazia. Você pode fazer chamadas aninhados aos membros em uma variável que contém um tipo complexo, por exemplo, `this.Address.State == "WA"`.

 O editor de condição de regra oferece suporte aos seguintes operadores:

- Operadores relacionais: ==, =! =

- Operadores de comparação: <, \<=, >, > =

- Operadores aritméticos: +, -, *,/, MODIFICAÇÃO

- Operadores lógicos: and, & &, ou &#124; &#124;,, não,!

- Operadores de bits-bit: &,&#124;

  Precedência de operadores de expressão segue regras de precedência de operador C#.

  O editor de condição de regra suporta as seguintes expressões numéricas:

  == 1D de this.i (resoluções a 1,0)

  == 1E1 de this.i (resoluções a 10,0)

  == 1L de this.i (resoluções como um longo)

  == 1M de this.i (resoluções como um decimal)

  == 1F de this.i (resoluções como um único)

  == 1U de this.i (resoluções como um unsigned int)

  Para obter mais informações sobre condições, consulte [usando condições em fluxos de trabalho](https://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Consulte também
 [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039) [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049) [caixa de diálogo de seleção de condição (herdada)](../workflow-designer/select-condition-dialog-box-legacy.md) [usando condições em fluxos de trabalho](https://go.microsoft.com/fwlink?LinkID=65009) [Designer herdado para ajuda da interface do usuário Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)