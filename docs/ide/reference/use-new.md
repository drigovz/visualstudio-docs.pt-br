---
title: Usar Novo ()
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b2091c046efac9f5676e5d2d99ef798283b95f6e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402252"
---
# <a name="use-new"></a>Use `new()`.

Isso se aplica a:

- C#

**O que:** Use o `new()` .

**Quando:** Você tem um campo que não pode usar `var` ou uma preferência de estilo de código para não usar `var` .

**Por que:** Portanto, você não precisa escrever código repetitivo repetindo o tipo duas vezes.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na declaração de campo.

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecione **usar ' novo (...) '** :

    ![Usar ' New (...) '](media/use-new.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
