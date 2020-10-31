---
title: Converter instrução If para alternar instrução ou expressão
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8e093325ff4a4e6a9f8a2623e7e42f69bb6fa62f
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102526"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Converter instrução if em instrução switch ou em expressão switch

Esta refatoração aplica-se a:

- C#

**O que:** Converta uma instrução If para uma [instrução switch](/dotnet/csharp/language-reference/keywords/switch) ou para a [expressão switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

**Quando:** Você deseja converter uma `if` instrução em uma `switch` instrução ou em uma `switch` expressão e vice-versa.

**Por que:** Se você estiver usando uma `if` instrução, essa refatoração permitirá uma transição fácil para `switch` instruções ou `switch` expressões.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na palavra-chave `if`.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas** .
3. Selecione uma das duas opções a seguir:

    Selecione **converter para a instrução ' switch '** .

   ![Conversão de instrução If para alternar](media/convert-if-to-switch-statement.png)

    Selecione **converter para expressão ' switch '** .

    ![Converter a instrução If para alternar a expressão](media/convert-if-to-switch-expression.png)

## <a name="see-also"></a>Veja também

- [Refatoração](../refactoring-in-visual-studio.md)
