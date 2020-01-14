---
title: Caixa de diálogo Editor de conjunto de regras (Herdado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8010bbbc38dee980ebe89dc60ccb513379103a26
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846321"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Caixa de diálogo do editor de regra (legados)
Este tópico descreve como usar a caixa de diálogo **Editor de conjunto de regras** no [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 A caixa de diálogo **Editor de conjunto de regras** é usada para criar e modificar conjuntos de regras [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) , que são serializados para um arquivo. Rules.

> [!NOTE]
> Se você quiser abrir o arquivo. Rules com o **Editor de XML com codificação**, você deve primeiro fechar a janela do designer associada para o fluxo de trabalho ou a atividade.

 Para obter informações sobre como acessar a caixa de diálogo **Editor de conjunto de regras** , consulte [como: criar um conjunto de regras PolicyActivity (Herdado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> O editor das regras de novas [!INCLUDE[wfd2](../includes/wfd2-md.md)] que é usado para direcionar [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] não oferece suporte Multitargeting.

 A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **Editor de conjunto de regras** .

|Elemento da interface|Descrição|
|----------------|-----------------|
|**Adicionar regra**|Adicione uma nova definição de regra ao conjunto de regras.|
|**Excluir**|Exclui a regra selecionada do conjunto de regras.|
|**Encadeamento**|Especifica que tipo de encadeamento frente para usar com o conjunto de regras. As opções disponíveis são:<br /><br /> -   **encadeamento completo**, que especifica o uso de todos os mecanismos de encadeamento de encaminhamento: implícito, atribuição de método e explícito usando uma função de **atualização** .<br />-   **sequencial**, que especifica não usar nenhum encadeamento de encaminhamento.<br />-   **somente atualização explícita**, que especifica a execução somente do encadeamento de encaminhamento em ações de **atualização** .<br /><br /> Para obter mais informações sobre encadeamento de encaminhamento, consulte [usando a atividade PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx).|
|**Nome**|Regra título da coluna da lista. Clique para classificar por nome a lista de regras.|
|**Priority**|Regra título da coluna da lista. Clique para classificar a lista de regras por prioridade.|
|**Reavaliação**|Regra título da coluna da lista. Clique para classificar a lista de regras pelo tipo de reavaliação.|
|**Visualização da regra**|Regra título da coluna da lista. Clique para classificar a lista de regras por visualização de condição e ações de uma regra.|
|**Name:**|Digite o nome da regra.|
|**Priority:**|Insira uma prioridade para a regra. A prioridade padrão é 0.|
|**Reavaliação**|Especifica que tipo de reavaliação de regras para usar com a regra. As opções disponíveis são:<br /><br /> -   **sempre**, o que faz com que a regra seja reavaliada conforme necessário.<br />-   **nunca**, o que faz com que a regra nunca seja reavaliada. Neste caso uma regra executa somente uma vez.|
|**Ativo**|Verifique para fazer a regra ativo.|
|**Problema**|Digite uma expressão para a condição de regra. Para obter informações sobre a sintaxe de expressão, consulte a seção “inserindo de expressões de condição e a ação” nessa página.|
|**Ações then:**|Insira a expressão para ações. Para obter informações sobre a sintaxe de expressão, consulte a seção “inserindo de expressões de condição e a ação” nessa página.|
|**Ações else:**|Insira a expressão para outras ações. Para obter informações sobre a sintaxe de expressão, consulte a seção “inserindo de expressões de condição e a ação” nessa página.|
|**OK**|Clique para salvar a regra definida como um arquivo de .rules.|

 Para obter mais informações sobre conjuntos de regras, consulte [usando a atividade PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="entering-condition-and-action-expressions"></a>Inserindo expressões de condição e de ação
 Você insere expressões para a condição e as ações then e else como texto em suas respectivas caixas de texto na caixa de diálogo **Editor de conjunto de regras** . Você pode digitar **isso.** no editor para fazer referência a campos, propriedades e métodos usados no fluxo de trabalho, usando um tipo de menu IntelliSense. Ou você pode digitar um nome de membro de fluxo de trabalho diretamente. Você pode chamar métodos estáticos em tipos referenciados digitando o nome da classe seguida do nome do método.

 Você pode adicionar operadores lógicos a condição, como AND, OU, e NOT. Você também pode adicionar predicados. Um predicado é um operador binário e dois operandos. Os operadores binários com suporte são = =, >, \<, > = e < =. Os operandos são suportados valor constante, função aritmética, e membros públicos o escopo.

 Você pode especificar o tipo para a comparação e pode comparar com uma cadeia de caracteres **nula** ou vazia. Você pode aninhar chamadas aos membros em uma variável que contém um tipo complexo, por exemplo, `this.Address.State == "WA"`.

 As expressões dão suporte aos seguintes operadores:

- Operadores relacionais: ==, =! =

- Operadores de comparação: <, \<=, >, > =

- Operadores aritméticos: +, -, *,/, MODIFICAÇÃO

- Operadores lógicos: and, & &, ou &#124; &#124;,, não,!

- Operadores de bits-bit: &,&#124;

  Precedência de operadores de expressão segue regras de precedência de operador C#.

  Para obter mais informações sobre condições, consulte [usando condições em fluxos de trabalho](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Interromper e atualizar funções
 Ações **then:** and **else:** expressões dão suporte a funções **Halt** e **Update** . Para usar a função **Halt** , digite **Halt** em uma **ação then:** ou **ação:** caixa de texto. A ação **parar** faz com que a execução do conjunto de regras pare imediatamente e o controle retorne ao código de chamada. Você usa a função **Update** com encadeamento de encaminhamento.

 Uma instrução **Update** pode ser expressa no editor em uma das duas formas; ambos os formulários são mostrados no exemplo a seguir:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Para obter mais informações sobre como usar **Update** com encadeamento de encaminhamento, consulte [usando a atividade PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="see-also"></a>Veja também
 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [Caixa de diálogo selecionar conjunto de regras (Herdado)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [usando a atividade PolicyActivity](https://msdn2.microsoft.com/library/bb675229.aspx) [usando condições em fluxos de trabalho](https://msdn2.microsoft.com/library/bb628447.aspx)
