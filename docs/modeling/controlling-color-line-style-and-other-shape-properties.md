---
title: Controlando cor, estilo de linha e outras propriedades de formas
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: ea0b73470bc9f3bed76328c55d823cef3c5b8e9e
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269313"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controlando cor, estilo de linha e outras propriedades de formas

Algumas propriedades da forma como a cor podem ser 'expostas'. Ou seja, as propriedades podem ser vinculadas a uma propriedade de domínio da forma. Outros têm a ser controlada diretamente.

## <a name="exposing-a-property"></a>Expor uma propriedade
 Algumas propriedades da forma como a cor podem ser vinculadas ao valor de uma propriedade de domínio.

 Na definição de DSL, selecione uma forma, conector ou classe de diagrama. No menu de atalho, escolha **adicionar exposto**e, em seguida, escolha a propriedade desejada, como cor de preenchimento.

 A forma agora tem uma propriedade de domínio que você pode definir no código do programa ou como um usuário.

## <a name="dynamically-updating-an-exposed-property"></a>Atualização dinâmica de uma propriedade exposta
 Normalmente você deseja tornar a propriedade exposta dependente de outra propriedade. Por exemplo, convém uma forma para ativar vermelho sempre que uma propriedade de domínio específico é menor que zero. Para tornar essa dependência, crie uma [regra](../modeling/rules-propagate-changes-within-the-model.md). Por exemplo:

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