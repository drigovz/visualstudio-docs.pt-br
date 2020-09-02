---
title: Controlando cor, estilo de linha e outras propriedades de forma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5d296f5ab3f5c584558b373b57c175fb2bacef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667849"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controlando cor, estilo de linha e outras propriedades de formas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Algumas propriedades de forma, como Color, podem ser ' expostas ' – ou seja, vinculadas a uma propriedade de domínio da forma. Outras pessoas precisam ser controladas diretamente.

## <a name="exposing-a-property"></a>Expondo uma propriedade
 Algumas propriedades de forma, como Color, podem ser vinculadas ao valor de uma propriedade de domínio.

 Na definição de DSL, selecione uma forma, um conector ou uma classe de diagrama. No menu de contexto, escolha **Adicionar exposto**e, em seguida, escolha a propriedade desejada, como cor de preenchimento.

 A forma agora tem uma propriedade Domain que pode ser definida no código do programa ou como um usuário.

## <a name="dynamically-updating-an-exposed-property"></a>Atualizando dinamicamente uma propriedade exposta
 Normalmente, você deseja tornar a propriedade exposta dependente de outra propriedade. Por exemplo, talvez você queira que uma forma fique vermelha sempre que uma propriedade de domínio específica for menor que zero. Para fazer essa dependência, crie uma [regra](../modeling/rules-propagate-changes-within-the-model.md). Por exemplo:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```
