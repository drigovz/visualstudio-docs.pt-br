---
title: Usar new()
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a129e94f6009eec51995b6a4e170f0a804e6407f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889805"
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

3. Selecione **usar ' novo (...) '**:

    ![Usar ' New (...) '](media/use-new.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
