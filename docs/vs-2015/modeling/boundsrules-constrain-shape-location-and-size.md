---
title: BoundsRules restringir o local e o tamanho da forma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672722"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules restringem o local e o tamanho de uma forma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma *regra de limites* é uma classe que define os limites de tamanho e local de uma forma. Ele fornece um método que é chamado repetidamente enquanto um usuário está arrastando uma forma ou os cantos ou os lados de uma forma.

 O exemplo a seguir restringe uma forma retangular a ser uma barra de tamanho fixo, tanto horizontal quanto vertical. Quando o usuário arrasta os cantos ou os lados, o contorno inverte entre as duas configurações permitidas de altura e largura.

 A regra de limites é uma classe derivada de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Uma instância da regra é criada na forma:

```
using Microsoft.VisualStudio.Modeling.Diagrams; ...
public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}
/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

 Observe que o local e o tamanho podem ser restritos se você desejar.

## <a name="see-also"></a>Consulte também
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> [responder e propagar alterações](../modeling/responding-to-and-propagating-changes.md)
