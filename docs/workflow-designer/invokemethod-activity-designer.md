---
title: Designer de atividade Designer de Fluxo de Trabalho-InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 593ec198cdfdd8acd1967abb046384711e1fa9ac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650164"
---
# <a name="invokemethod-activity-designer"></a>Designer de atividade de InvokeMethod

O **InvokeMethod** designer é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.InvokeMethod>.

## <a name="the-invokemethod-activity"></a>A atividade InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> chama um método público de um objeto ou tipo especificado.

### <a name="use-the-invokemethod-activity-designer"></a>Usar o designer de atividade InvokeMethod

Acesse o designer de atividade **InvokeMethod** na categoria **primitivos** da **caixa de ferramentas**. O designer de atividade **InvokeMethod** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho onde as atividades sempre são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Descartar o designer de atividade cria uma atividade de <xref:System.Activities.Statements.InvokeMethod> com um <xref:System.Activities.Activity.DisplayName%2A> padrão de InvokeMethod. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **InvokeMethod** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-invokemethod-properties"></a>As Propriedades InvokeMethod

A tabela a seguir mostra as propriedades <xref:System.Activities.Statements.InvokeMethod> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas podem ser editadas na superfície Designer de Fluxo de Trabalho.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.InvokeMethod> . O valor padrão é InvokeMethod.<br /><br /> Embora o <xref:System.Activities.Activity.DisplayName%2A> não seja estritamente necessário, é melhor usar um.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|verdadeiro|O nome do método a ser chamado quando a atividade executar. O método chamado deve ser declarado como **público**. Essa propriedade pode ser editada na superfície do designer e é obrigatória.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|A coleção de parâmetros do método chamado. Os parâmetros devem ser adicionados à coleção na mesma ordem que eles aparecem na assinatura de método. Para exibir a caixa de diálogo de **parâmetros** onde você pode definir essa propriedade, clique no botão de reticências no campo **parâmetros** da grade de propriedades. Clique no botão **criar argumento** para adicionar os parâmetros.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|O valor de retorno de chamada de método.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|verdadeiro|Especifica se o método é chamado de forma assíncrona. O valor padrão é **false**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|O objeto que contém o método para chamar. Esta propriedade pode ser editada na superfície de designer.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> ou <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> são necessários para ser definidos.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|O tipo de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Esta propriedade pode ser editada na superfície de designer. Esta propriedade deve ser definida somente se o método é chamado estático.|

Para passar parâmetros como um C# parâmetro **out** (por exemplo, `Method1(out myParam))`, use **OutArgument** em vez de **InOutArgument**

Métodos com argumentos chamados **TargetObject** ou **Result** não podem ser invocados usando a atividade <xref:System.Activities.Statements.InvokeMethod>. A razão para isso é que registros de atividade de <xref:System.Activities.Statements.InvokeMethod><xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> e <xref:System.Activities.Statements.InvokeMethod.Result%2A> em <xref:System.Activities.Activity.CacheMetadata%2A>.

O algoritmo para registrar os parâmetros em <xref:System.Activities.Activity.CacheMetadata%2A> é mostrado na lista a seguir:

1. Argumento de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> do registro.

2. Argumento de <xref:System.Activities.Statements.InvokeMethod.Result%2A> do registro.

3. Iterar através da coleção de <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> e registrar cada argumento.

A exceção resultante é do tipo <xref:System.Activities.InvalidWorkflowException> com a seguinte mensagem: “InvokeMethod”: Uma variável, RuntimeArgument ou um DelegateArgument já existem com o nome “TargetObject”. Nomes devem ser exclusivos dentro do escopo de ambiente.

Essa restrição não se aplica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> e <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Eles não são argumentos de fluxo de trabalho e, portanto, não são registrados na coleção de <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> da atividade <xref:System.Activities.Statements.InvokeMethod> no método <xref:System.Activities.Activity.CacheMetadata%2A>.

## <a name="see-also"></a>Consulte também

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Atribuir](../workflow-designer/assign-activity-designer.md)
- [Atrasar](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)