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
monikerRange: vs-2019
ms.openlocfilehash: 58d2757fa8798b67c8e597f5f82bc65a279f4a90
ms.sourcegitcommit: 8ff6c6975148ce43bdac21c8995fbab910c312fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2020
ms.locfileid: "80375561"
---
# <a name="move-type-to-namespace"></a>Mover tipo para namespace

Esta refatoração aplica-se a:

- C#

**O que é isso?** Mova o tipo para namespace.

**Quando:** Você deseja mover um tipo para um namespace ou pasta diferente. 

**Por que:** Você deseja refatorar partes da sua solução e ter uma maneira rápida de mover um tipo para um namespace ou pasta diferente. 

## <a name="how-to"></a>Como fazer

1. Coloque o cursor no nome da classe.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Mover para o namespace**.

   ![Mover para a refatoração de namespace](media/move-to-namespace.png)

4. Na caixa de diálogo que é aberta, selecione o namespace de destino para o qual você deseja mover o tipo. 

   ![Selecione uma caixa de diálogo de namespace](media/select-target-namespace.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
