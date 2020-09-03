---
title: Converter instrução if em instrução switch ou em expressão switch
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094128"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Converter instrução if em instrução switch ou em expressão switch

Esta refatoração aplica-se a:

- C#

**O que:** Converta uma instrução If para uma [instrução switch](/dotnet/csharp/language-reference/keywords/switch) ou para a [expressão switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

**Quando:** Você deseja converter uma `if` instrução em uma `switch` instrução ou em uma `switch` expressão e vice-versa. 

**Por que:** Se você estiver usando uma `if` instrução, essa refatoração permitirá uma transição fácil para `switch` instruções ou `switch` expressões.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na palavra-chave `if`.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione uma das duas opções a seguir: 

    Selecione **converter para a instrução ' switch '**.

   ![Conversão de instrução If para alternar](media/convert-if-to-switch-statement.png) 

    Selecione **converter para expressão ' switch '**. 

    ![Converter a instrução If para alternar a expressão](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
