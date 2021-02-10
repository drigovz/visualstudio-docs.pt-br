---
title: Como implementar uma interface (Designer de Classe)
description: Saiba como implementar uma interface no diagrama de classe conectando-a a uma classe que fornece código para os métodos de interface.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 358d099839c42c20b47b850b84dc3dd307855b3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951882"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Como implementar uma interface no Designer de Classe

No **Designer de Classe**, você pode implementar uma interface no diagrama de classe conectando-a a uma classe que forneça código para os métodos da interface. **Designer de classe** gera uma implementação de interface e exibe a relação entre a interface e a classe como uma relação de herança. É possível implementar uma interface desenhando uma linha de herança entre a interface e a classe ou arrastando a interface do Modo de Exibição de Classe.

> [!TIP]
> Você pode criar interfaces da mesma maneira como cria outros tipos. Se a interface existir, mas não aparecer no diagrama de classe, exiba-a primeiro. Para obter mais informações, consulte [como: criar tipos usando Designer de classe](how-to-create-types.md) e [como exibir tipos existentes](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Para implementar uma interface desenhando uma linha de herança

1. No diagrama de classe, exiba a interface e a classe que a implementará.

2. Desenhe uma linha de herança da classe e da interface.

     Um pirulito aparece anexado à classe, e um rótulo com o nome da interface identifica a relação de herança. O Visual Studio gera stubs para todos os membros da interface.

Para obter mais informações, consulte [como: criar herança entre tipos](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Para implementar uma interface da janela do Modo de Exibição de Classe

1. No diagrama de classe, exiba a classe cuja interface você deseja implementar.

2. Abra **modo de exibição de classe** e localize a interface.

    > [!TIP]
    > Se o **Modo de Exibição de Classe** não estiver aberto, abra o **Modo de Exibição de Classe** no menu **Exibir** ou pressione **Ctrl**+**Shift**+**C**.

3. Arraste o nó da interface para a forma de classe no diagrama.

     Um pirulito aparece anexado à classe, e um rótulo com o nome da interface identifica a relação de herança. O Visual Studio gera stubs para todos os membros da interface. Neste ponto, a interface é implementada.

## <a name="see-also"></a>Consulte também

- [Como criar tipos usando o Designer de Classe](how-to-create-types.md)
- [Como exibir tipos existentes](how-to-view-existing-types.md)
- [Como criar herança entre tipos](how-to-create-inheritance-between-types.md)
- [Refatorando classes e tipos](refactoring-classes-and-types.md)
