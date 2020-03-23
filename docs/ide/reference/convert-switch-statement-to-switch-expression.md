---
title: Converter instrução switch em expressão switch
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cc13cffe8352d9fb57f5bb991c3af615eddb2a14
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68740055"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Converter instrução switch em expressão switch

Esta refatoração aplica-se a:

- C#

**O que é isso?** Converta uma [indade de switch](/dotnet/csharp/language-reference/keywords/switch) em uma [expressão de switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8.0 .

**Quando:** Você quer converter `switch` uma `switch` declaração em uma expressão e vice-versa. 

**Por que:** Se você estiver usando apenas expressões, essa refatoração permite uma transição fácil das declarações tradicionais. `switch`

## <a name="how-to"></a>Como fazer

1. No arquivo de projeto, [defina a versão da linguagem como versão prévia](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file), uma vez que as expressões `switch` são um novo recurso do C# 8.0.
2. Coloque o cursor `switch` na palavra-chave e **pressione Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Converter instrução switch em expressão**.

   ![Converter instrução switch em expressão switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
