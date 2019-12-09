---
title: Personalizando ferramentas de elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655016"
---
# <a name="customizing-element-tools"></a>Ferramentas de elemento personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em algumas definições de DSL, você representa um único conceito como um grupo de elementos. Por exemplo, se você criar um modelo no qual um componente tem um conjunto fixo de portas, sempre deseja que as portas sejam criadas ao mesmo tempo que o componente pai. Portanto, você precisa personalizar a ferramenta de criação de elementos para que ele crie um grupo de elementos em vez de apenas um. Para conseguir isso, você pode personalizar como a ferramenta de criação de elementos é inicializada.

 Você também pode substituir o que acontece quando a ferramenta é arrastada para o diagrama ou para um elemento.

## <a name="customizing-the-content-of-an-element-tool"></a>Personalizando o conteúdo de uma ferramenta de elemento
 Cada ferramenta de elemento armazena uma instância de um <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), que contém uma versão serializada de um ou mais elementos e links de modelo. Por padrão, o EGP de uma ferramenta de elemento contém uma instância da classe que você especifica para a ferramenta. Você pode alterar isso substituindo *YourLanguage* `ToolboxHelper.CreateElementToolPrototype`. Esse método é chamado quando o pacote de DSL é carregado.

 Um parâmetro do método é a ID da classe que você especificou na definição de DSL. Quando o método é chamado com a classe em que você está interessado, você pode adicionar elementos extras ao EGP.

 O EGP deve incluir links de inserção de um elemento principal para os elementos subsidiários. Ele também pode incluir links de referência.

 O exemplo a seguir cria um elemento principal e dois elementos incorporados. A classe principal é chamada de resistência, e tem duas relações de incorporação aos elementos chamados terminal. As propriedades da função de incorporação são nomeadas Terminal1 e Terminal2, e ambas têm uma multiplicidade de 1.. 1.

```
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>Consulte também
 [Personalizando a criação e o movimento de elementos](../modeling/customizing-element-creation-and-movement.md)
