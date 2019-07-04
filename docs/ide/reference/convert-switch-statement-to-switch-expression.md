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
ms.openlocfilehash: ecb7750301101a2607c17e68b5e919623a03caba
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329033"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Converter instrução switch em expressão switch

Esta refatoração aplica-se a:

- C#

**O quê:** Converta uma [instrução switch](/dotnet/csharp/language-reference/keywords/switch) em uma [expressão switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) C# 8.0.

**Quando:** Você deseja converter uma instrução `switch` em uma expressão `switch` e vice-versa. 

**Por que:** Se você estiver usando apenas expressões, esta refatoração permitirá uma transição fácil das instruções `switch` tradicionais.

## <a name="how-to"></a>Como fazer

1. No arquivo de projeto, [defina a versão da linguagem como versão prévia](/dotnet/csharp/language-reference/configure-language-version#set-the-language-version-in-visual-studio), uma vez que as expressões `switch` são um novo recurso do C# 8.0.
2. Coloque o cursor na palavra-chave `switch` e pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Converter instrução switch em expressão**.

   ![Converter instrução switch em expressão switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
