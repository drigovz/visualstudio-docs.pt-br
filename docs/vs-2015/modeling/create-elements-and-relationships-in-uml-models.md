---
title: Criar elementos e relações em modelos UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ea066aa31cbc1f6408ee55c92a5ca761608f534
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667821"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>Criar elementos e relações em modelos UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No código do programa para uma extensão do Visual Studio, você pode criar e excluir elementos e relações.

## <a name="create-a-model-element"></a>Criar um elemento de modelo

### <a name="namespace-imports"></a>Importações de namespace
 Você deve incluir as instruções a seguir `using` .

 Os métodos de criação são definidos como métodos de extensão neste namespace:

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Obter o proprietário do elemento que você deseja criar
 Um modelo forma uma única árvore, para que cada item tenha um proprietário, com exceção da raiz do modelo. A raiz do modelo é do tipo `IModel` , que é um tipo de `IPackage` .

 Se você estiver criando um elemento que será exibido em um diagrama específico, por exemplo, o diagrama atual do usuário, você geralmente deverá criá-lo no pacote vinculado a esse diagrama. Por exemplo:

```
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;
```

 Esta tabela resume a propriedade de elementos de modelo comuns:

|Elemento a ser criado|Proprietário|
|---------------------------|-----------|
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|
|`IAttribute, IOperation`|`IClass, IInterface`|
|`IPart, IPort`|`IComponent`|
|`IAction, IObjectNode`|`IActivity`|
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|

### <a name="invoke-the-create-method-on-the-owner"></a>Invocar o método Create no proprietário
 O nome do método é do formato: de `Create` *Propriedade* `()` . Por exemplo:

```
IUseCase usecase1 = linkedPackage.CreateUseCase();
```

 Alguns tipos têm métodos de criação mais complexos, especialmente em diagramas de sequência. Consulte [Editar diagramas de sequência UML usando a API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Para alguns tipos de elemento, você pode alterar o proprietário de um elemento durante seu tempo de vida, usando `SetOwner(newOwner)` .

### <a name="set-the-name-and-other-properties"></a>Definir o nome e outras propriedades

```
usecase1.Name = "user logs in";
```

### <a name="example"></a>Exemplo

```
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Extensions;
...
 void InstantiateObserverPattern (IPackage package, string namePrefix)
 {    IInterface observer = package.CreateInterface();
      observer.Name = namePrefix + "Observer";
      IOperation operation = observer.CreateOperation();
      operation.Name = "Update";
      IClass subject = package.CreateClass();
      subject.Name = namePrefix + "Subject"; ...
```

## <a name="create-an-association"></a>Criar uma associação

#### <a name="to-create-an-association"></a>Para criar uma associação

1. Obtenha o proprietário da associação, que geralmente é o pacote ou modelo que contém a extremidade de origem da relação.

2. Invoque o método Create necessário no proprietário.

3. Defina as propriedades da relação, como seu nome.

     Por exemplo:

    ```
    IAssociation association = subject.Package.CreateAssociation(subject, observer);
    association .Name = "Observes";
    ```

4. Defina as propriedades de cada extremidade da relação. Sempre há dois `MemberEnds` . Por exemplo:

    ```
    association .MemberEnds[0].Name = "subject";   // role name
    association .MemberEnds[1].Name = "observers"; // role name
    association .MemberEnds[1].SetBounds("0..*");
                // multiplicity defaults to "1"
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;
    ```

## <a name="create-a-generalization"></a>Criar uma generalização

```
IGeneralization generalization =
  subclass.CreateGeneralization(superClass);
```

## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Excluir um elemento, uma relação ou uma generalização do modelo

```
anElement.Delete();
```

 Quando você exclui um elemento de um modelo:

- Todas as relações que são vinculadas a ela também são excluídas.

- Todas as formas que a representavam em um diagrama também são excluídas.

## <a name="see-also"></a>Consulte Também
 [Estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md) [exibir um modelo UML em diagramas](../modeling/display-a-uml-model-on-diagrams.md)
