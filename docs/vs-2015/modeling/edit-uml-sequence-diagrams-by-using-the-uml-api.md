---
title: Editar diagramas de sequência UML usando a API UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d0bebbb4e6dfe25ce9834595be11aad0fd1f1ba0
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871878"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Editar diagramas de sequência UML usando a API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma interação é uma sequência de mensagens entre um conjunto de linhas de vida. Uma interação é exibida em um diagrama de sequência UML.

 Para obter detalhes completos da API, consulte [Microsoft. VisualStudio. Uml.](/previous-versions/dd493373(v=vs.140))Interactions.

 Para obter uma introdução mais geral para escrever comandos e manipuladores de gestos para diagramas UML, consulte [definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="basic-code"></a>Código básico

### <a name="namespace-imports"></a>Importações de namespace
 Você deve incluir as seguintes `using` instruções:

```
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types such as IPackage
using Microsoft.VisualStudio.Uml.Interactions;
   // for interaction types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // to create elements and use additional functions
```

 Se você estiver criando comandos de menu e manipuladores de gestos, também será necessário:

```
using System.ComponentModel.Composition;
   // for Import and Export
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   // for diagrams and context
```

 Para obter mais informações, consulte [definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

### <a name="getting-the-context"></a>Obtendo o contexto
 Se você estiver editando uma interação como parte de um manipulador de comando ou de gesto em um diagrama de sequência, poderá obter uma referência ao contexto. Por exemplo:

```
[SequenceDesignerExtension]
[Export(typeof(ICommandExtension))]
public class MySequenceDiagramCommand : ICommandExtension
{
    [Import]
    public IDiagramContext Context { get; set; }
    public void QueryStatus (IMenuCommand command)
    {
      ISequenceDiagram sequenceDiagram =
          Context.CurrentDiagram as ISequenceDiagram;
         ...
```

### <a name="generated-and-uml-sequence-diagrams"></a>Diagramas de sequência gerados e UML
 Há dois tipos de diagramas de sequência: aqueles que são criados manualmente em um projeto de modelagem UML e aqueles que foram gerados a partir do código do programa. Use a `UmlMode` propriedade para descobrir qual diagrama de sequência você tem.

> [!NOTE]
> Essa propriedade retorna false somente para diagramas de sequência gerados a partir de código usando Visual Studio 2013 e anterior. Isso inclui diagramas de sequência gerados por código migrados do 2013 e anterior. Esta versão do Visual Studio não dá suporte à geração de novos diagramas de sequência.

 Por exemplo, se você quiser criar um comando de menu que só seja visível em diagramas de sequência UML, `QueryStatus()` o método poderá incluir a seguinte instrução:

```
command.Enabled = command.Visible =
      sequenceDiagram != null && sequenceDiagram.UmlMode;
```

 Em um diagrama de sequência gerado, linhas de vida, mensagens e outros elementos são, na maioria das vezes, os mesmos de um diagrama de sequência UML. Em um modelo UML, o repositório de modelos tem uma raiz, que é o modelo que possui todos os outros elementos. Mas uma interação gerada existe em seu próprio repositório de modelos, que tem uma raiz nula:

```
IModel rootModel = sequenceDiagram.ModelStore.Root;
    // !sequenceDiagram.UmlMode == (rootModel == null)
```

## <a name="to-create-and-display-an-interaction"></a>Para criar e exibir uma interação
 Crie a interação como um filho de um pacote ou modelo.

 Por exemplo, se você estiver desenvolvendo um comando que pode ser executado em um diagrama de sequência em branco, sempre deverá começar verificando se a interação existe.

```
public void Execute (IMenuCommand command)
{
    ISequenceDiagram sequenceDiagram =
         Context.CurrentDiagram as ISequenceDiagram;
    if (sequenceDiagram == null) return;
    // Get the diagram's interaction:
    IInteraction interaction = sequenceDiagram.Interaction;
    // A new sequence diagram might have no interaction:
    if (interaction == null)
    {
       // Get the home package or model of the diagram:
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();
       interaction = parentPackage.CreateInteraction();
       // Display the interaction on the sequence diagram:
       sequenceDiagram.Bind(interaction);
    }
```

## <a name="updating-an-interaction-and-its-layout"></a>Atualizando uma interação e seu layout
 Ao atualizar uma interação, sempre Finalize a operação atualizando seu layout usando um dos seguintes métodos:

- `ISequenceDiagram.UpdateShapePositions()`ajusta as posições das formas que foram inseridas ou movidas recentemente e suas formas vizinhas.

- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])`redesenha todo o diagrama. Você pode usar o parâmetro para especificar o reposicionamento das linhas de vida, as mensagens ou ambas.

  Isso é particularmente importante quando você insere novos elementos ou move os elementos existentes. Elas não estarão nas posições corretas no diagrama até que você tenha executado uma dessas operações. Você só precisa chamar uma dessas operações uma vez ao final de uma série de alterações.

  Para evitar bemusing o usuário que executa um desfazer após o comando, use um `ILinkedUndoTransaction` para colocar suas alterações e o final `Layout()` ou `UpdateShapePositions()` as operações. Por exemplo:

```
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))
{
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);
  Diagram.UpdateShapePositions();
  transaction.Commit();
}
```

 Para usar um `ILinkedUndoTransaction`, você deve fazer essa declaração em sua classe:

```
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }
```

 Para obter mais informações, consulte [vincular atualizações de modelo UML usando transações](../modeling/link-uml-model-updates-by-using-transactions.md).

## <a name="building-an-interaction"></a>Criando uma interação

### <a name="to-create-lifelines"></a>Para criar linhas de vida

```
ILifeline lifeline = interaction.CreateLifeline();
```

 Uma linha de vida representa um elemento que poderia ser conectado, ou seja, uma instância de um tipo. Por exemplo, se a interação for usada para mostrar como um componente Delega mensagens de entrada para suas partes internas, as linhas de vida podem representar as portas e partes do componente:

```
foreach (IConnectableElement part in
            component.Parts
           .Concat<IConnectableElement>(component.OwnedPorts))
{
   ILifeline lifeline = interaction.CreateLifeline();
   lifeline.Represents = part;
}
```

 Como alternativa, se a interação mostrar um conjunto arbitrário de objetos, você poderá criar uma propriedade ou outra `IConnectableElement` na própria interação:

```
ILifeline lifeline = interaction.CreateLifeline();
IProperty property1 = interaction.CreateProperty();
property1.Type = model.CreateInterface();
property1.Type.Name = "Type 1";
lifeline.Represents = property1;
```

 Como alternativa adicional, você pode definir o nome e o tipo de uma linha da vida sem vinculá-la a um elemento que pode ser conectado:

```
ILifeline lifeline = interaction.CreateLifeline();
lifeline.Name = "c1";
lifeline.SetInstanceType("Customer");
System.Diagnostics.Debug.Assert(
           lifeline.GetDisplayName() == "c1:Customer"  );
```

### <a name="to-create-messages"></a>Para criar mensagens
 Para criar uma mensagem, você deve identificar os pontos de inserção nas linhas de vida de origem e de destino. Por exemplo:

```
interaction.CreateMessage( sourceInsertionPoint,
                           targetInsertionPoint,
                           MessageKind.Complete,
                           MessageSort.ASynchCall)
```

 Para criar uma mensagem que tenha um destino indefinido ou de origem indefinido:

```
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);
```

 Há várias mensagens que você pode usar para identificar pontos de inserção em todos os pontos-chave em uma linha de vida:

|Método em ILifeline|Use-o para inserir neste ponto|
|-------------------------|------------------------------------|
|`FindInsertionPointAtTop()`|A parte superior da linha de vida.|
|`FindInsertionPointAtBottom()`|A parte inferior da linha de vida.|
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Um ponto imediatamente após a mensagem especificada.|
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|O ponto pode estar na linha da vida ou em um bloco de especificação de execução pai.|
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Um ponto após um uso de interação.|
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Um ponto após um fragmento combinado.|
|`FindInsertionPoint(IExecutionSpecification block)`|A parte superior de um bloco de execução.|
|`FindInsertionPoint(IInteractionOperand fragment)`|A parte superior de um operando de um fragmento combinado.|

 Ao criar mensagens, tome cuidado para evitar a definição de uma mensagem que seria cruzada por outra mensagem.

### <a name="to-create-combined-fragments-and-interaction-uses"></a>Para criar fragmentos combinados e usos de interação
 Você pode criar fragmentos combinados e usos de interação especificando um ponto de inserção em cada linha da vida que deve ser coberta pelo elemento. Tome cuidado para evitar a especificação de um conjunto de pontos que ultrapassaram uma mensagem ou fragmento existente.

```
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
Interaction.CreateInteractionUse(
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));
```

 Você também pode criar um fragmento combinado que cubra um conjunto existente de mensagens. Todas as mensagens devem ser originadas na mesma linha da vida ou no mesmo bloco de execução.

```
ICombinedFragment cf = Interaction.CreateCombinedFragment(
  InteractionOperatorKind.Loop,
  Interaction.Lifelines.First().GetAllOutgoingMessages());
```

 Um fragmento combinado é sempre criado com um único operando. Para criar um novo operando, você deve especificar o operando existente que deseja inserir antes ou depois, e se deseja inserir depois dele ou antes:

```
// Create an additional operand before the first
cf.CreateInteractionOperand(cf.Operands.First(), false);
// Create an additional operand after the last:
cf.CreateInteractionOperand(cf.Operands.Last(), true);
```

## <a name="troubleshooting"></a>Solução de problemas
 As formas serão exibidas em posições incorretas se as alterações não `UpdateShapePositions()` forem `Layout()` concluídas com uma operação ou.

 A maioria dos outros problemas são causados por pontos de inserção sendo desalinhados, para que novas mensagens ou fragmentos precisem atravessar outras pessoas. Os sintomas podem ser que nenhuma alteração é executada ou uma exceção é lançada. A exceção pode não ser lançada até que `UpdateShapePositions()` a `Layout()` operação ou seja executada.

## <a name="see-also"></a>Consulte também

- [Microsoft. VisualStudio. Uml. interações](/previous-versions/dd493373(v=vs.140))
- [Estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
- [Definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
- [Definir um item de caixa de ferramentas de modelagem personalizada](../modeling/define-a-custom-modeling-toolbox-item.md)
- [Definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)
- [Programando com a API UML](../modeling/programming-with-the-uml-api.md)
