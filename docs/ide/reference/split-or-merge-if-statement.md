---
title: Dividir ou mesclar instruções if
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 405ccd4bc0197ce06aa14982a16dc02f6d13a537
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160732"
---
# <a name="split-or-merge-if-statements"></a>Dividir ou mesclar instruções if

Esta refatoração aplica-se a:

- C#

**O quê:** **O quê:** Dividir ou mesclar instruções [if](/dotnet/csharp/language-reference/keywords/if-else).

**Quando:** Você desejar dividir uma instrução `if` que usa os operadores `&&` e `||` em uma instrução `if` aninhada, ou mesclar uma instrução `if` com uma instrução `if` externa.

**Por que:** É uma questão de preferência de estilo.  

## <a name="how-to"></a>Como fazer

Se você quiser dividir a instrução `if`:

1. Coloque o cursor na instrução `if` pelo operador `&&` ou `||`.

2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.

    ![Dividir instrução if](../media/split-if-statement.png)

3. Selecione **Dividir em instruções if aninhadas**.

    ![Dividir instrução if concluída](../media/split-if-statement-complete.png)

Se você deseja mesclar a instrução `if` interna com a instrução `if` externa: 

1. Coloque o cursor na palavra-chave `if` interna.

2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.

    ![Mesclar instrução If](../media/merge-if-statement.png)

3. Selecione **Mesclar com instrução if externa**.

    ![Mesclar instrução if concluída](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)