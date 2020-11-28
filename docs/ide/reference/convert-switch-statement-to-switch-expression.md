---
title: Converter instrução switch em expressão switch
description: Saiba como usar o menu ações rápidas e refatoração para converter uma instrução switch em uma expressão de comutador C# 8,0.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: add43010fcec04cbe12889672f561f22057efb8c
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305523"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Converter instrução switch em expressão switch

Esta refatoração aplica-se a:

- C#

**O que:** Converta uma [instrução switch](/dotnet/csharp/language-reference/keywords/switch) em uma [expressão switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

**Quando:** Você deseja converter uma `switch` instrução em uma `switch` expressão e vice-versa. 

**Por que:** Se você estiver usando apenas expressões, essa refatoração permitirá uma transição fácil de `switch` instruções tradicionais.

## <a name="how-to"></a>Como fazer

1. No arquivo de projeto, [defina a versão da linguagem como versão prévia](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file), uma vez que as expressões `switch` são um novo recurso do C# 8.0.
2. Coloque o cursor na `switch` palavra-chave e pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Converter instrução switch em expressão**.

   ![Converter instrução switch em expressão switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
