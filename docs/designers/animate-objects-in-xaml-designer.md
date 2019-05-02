---
title: Animar objetos no XAML Designer
ms.date: 04/11/2018
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: a5bd9c24351201d066f9055554468939df02b33e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927018"
---
# <a name="animate-objects-in-xaml-designer"></a>Animar objetos no XAML Designer

É possível criar animações curtas que movem objetos ou fazer com que eles esmaeçam.

Para começar, crie um *storyboard*. Um storyboard contém uma ou mais *linhas do tempo*. Defina os *quadros chave* em uma linha do tempo para marcar as alterações de propriedade. Depois, ao executar a animação, o Blend interpolará as alterações de propriedade durante o período de tempo designado. O resultado é uma transição suave. É possível animar qualquer propriedade que pertença a um objeto, mesmo propriedades não visuais.

A ilustração a seguir mostra um storyboard denominado **MoveUp**. A linha do tempo contém quadros chave que marcam as posições X e Y de um retângulo. Quando essa animação é executada, o retângulo move de uma posição para outra sem problemas.

![Storyboard MoveUp no Designer XAML](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>Consulte também

- [Criar uma interface do usuário usando o Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)