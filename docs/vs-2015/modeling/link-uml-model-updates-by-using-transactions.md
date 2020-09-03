---
title: Vincular atualizações de modelo UML usando transações | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8930bba76830a6116c3182f3fb2936cd4f1a3e47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657604"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Vincular atualizações de modelo UML usando transações
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao definir uma extensão para os designers UML no Visual Studio, você pode agrupar várias alterações em uma única transação chamada contexto de *desfazer vinculado*. Para ver quais versões do Visual Studio oferecem suporte a modelos UML, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Por padrão, cada modificação que seu código faz em um modelo pode ser desfeita separadamente pelo usuário. Por exemplo, se você definir um comando de menu que permuta os nomes de duas classes UML, um usuário poderá invocar o comando e, em seguida, executar um único desfazer. Isso desfazeria a alteração em um nome, mas não no outro, deixando seu modelo em um estado não intencional.

 Para evitar isso, seu código pode executar uma série de alterações em uma transação. Isso faz com que as alterações pareçam uma única alteração para o usuário. Um comando desfazer subsequente irá desfazer a série inteira.

 Um benefício adicional é que seu código pode desfazer um conjunto parcialmente completo de alterações lançando uma exceção ou anulando a transação.

## <a name="to-group-changes-into-a-single-transaction"></a>Para agrupar alterações em uma única transação
 Verifique se as referências do projeto incluem este assembly .NET:

 **Microsoft. VisualStudio. Modeling. Sdk. [versão]. dll**

 Dentro de sua classe, declare uma propriedade importada que tenha o tipo <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext> :

 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`

 `...`

 `class … {`

 `[Import]`

 `public ILinkedUndoContext LinkedUndoContext { get; set; }`

 Em um método que modifica o modelo, coloque as alterações em uma transação:

 `using (ILinkedUndoTransaction transaction =`

 `LinkedUndoContext.BeginTransaction("my updates"))`

 `{`

 `// code to update model elements or shapes goes here`

 `transaction.Commit();`

 `}`

 Observe o seguinte:

- Você deve sempre incluir `Commit()` no final da transação. Se uma transação for descartada sem ser confirmada, a transação será revertida. Ou seja, o modelo será restaurado para seu estado no início da transação.

- Se ocorrer uma exceção que não é detectada dentro da transação, a transação será revertida. É um padrão frequente para colocar o `using` bloco da transação dentro de um `try…catch` bloco.

- Você pode aninhar transações.

- Você pode fornecer qualquer nome que não seja em branco para `BeginTransaction()` .

- Somente o repositório de modelos UML é afetado por essas transações. As transações de modelagem não afetam: variáveis, repositórios externos, como arquivos e bancos de dados, diagramas de camadas e modelos de código.

## <a name="example"></a>Exemplo

```
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Interfaces;
    using Microsoft.VisualStudio.Uml.Classes;
    using Microsoft.VisualStudio.Uml.Extensions;
    using System.Linq;
    using System.ComponentModel.Composition;
 ...
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  public void Execute(IMenuCommand command)
  {
    var selectedShapes =
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;
    string firstName = firstElement.Name;
    // Perform changes inside a transaction so that undo
    // works as a single change.
    using (ILinkedUndoTransaction transaction =
      LinkedUndoContext.BeginTransaction("Swap names"))
    {
        firstElement.Name = lastElement.Name;
        lastElement.Name = firstName;
        transaction.Commit();
    }
 }
```

## <a name="see-also"></a>Consulte Também
 [Programação com a API UML](../modeling/programming-with-the-uml-api.md) [definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
