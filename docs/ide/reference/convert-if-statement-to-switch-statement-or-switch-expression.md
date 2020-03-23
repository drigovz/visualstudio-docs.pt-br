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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094128"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Converter instrução if em instrução switch ou em expressão switch

Esta refatoração aplica-se a:

- C#

**O que é isso?** Converta uma indação if em uma [declaração de switch](/dotnet/csharp/language-reference/keywords/switch) ou na [expressão do switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8.0 .

**Quando:** Você deseja converter `if` uma `switch` declaração `switch` em uma declaração ou uma expressão e vice-versa. 

**Por que:** Se você estiver `if` usando uma instrução, essa `switch` refatoração permite uma transição fácil para declarações ou `switch` expressões.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na palavra-chave `if`.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione entre as duas opções a seguir: 

    Selecione **Converter para 'switch' .**

   ![Converter se a declaração para a declaração de switch](media/convert-if-to-switch-statement.png) 

    Selecione **Converter para 'alternar' expressão**. 

    ![Converta se a declaração para mudar a expressão](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
