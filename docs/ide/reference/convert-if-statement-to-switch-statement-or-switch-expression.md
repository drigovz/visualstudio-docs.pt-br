---
title: Converter instrução If para alternar instrução ou expressão switch
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280778"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Converter instrução If para alternar instrução ou expressão switch

Esta refatoração aplica-se a:

- C#

**O que:** Converta uma instrução If para uma [instrução switch](/dotnet/csharp/language-reference/keywords/switch) ou para C# a [expressão switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)8,0.

**Quando:** Você deseja converter uma instrução `if` em uma instrução `switch` ou em uma expressão de `switch` e vice-versa. 

**Por que:** Se você estiver usando uma instrução `if`, essa refatoração permitirá uma transição fácil para `switch` instruções ou `switch` expressões.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na palavra-chave `if`.
2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **converter para a instrução ' switch '** .

   ![Converter instrução If para alternar instrução ou expressão switch](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
