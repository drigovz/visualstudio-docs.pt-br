---
title: Mover tipo para namespace
ms.date: 06/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 821e915a0b66f25c5b89a83b31e93b01aea6f400
ms.sourcegitcommit: b593bb889f049fcbdff502c30b73178ed17dbdf0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67292702"
---
# <a name="move-type-to-namespace"></a>Mover tipo para namespace

Esta refatoração aplica-se a:

- C#

**O quê:** Mover tipo para namespace.

**Quando:** Você deseja mover um tipo para uma pasta ou namespace diferente. 

**Por que:** Você deseja refatorar partes de sua solução e ter uma maneira rápida de mover um tipo para um namespace ou pasta diferente. 

## <a name="how-to"></a>Como fazer

1. Coloque o cursor no nome da classe.
2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Mover para o namespace**.

   ![Mover para a refatoração de namespace](media/move-to-namespace.png)

4. Na caixa de diálogo que é aberta, selecione o namespace de destino para o qual você deseja mover o tipo. 

   ![Selecione uma caixa de diálogo de namespace](media/select-target-namespace.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
