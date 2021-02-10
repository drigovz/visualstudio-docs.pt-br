---
title: Converter instrução If para alternar instrução ou expressão
description: Saiba como usar o menu ações rápidas e refatoração para converter uma instrução If em uma instrução switch ou em uma expressão de comutador C# 8,0.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0d857338eb1c9b5bb66ccb89e20e6f892944d608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936823"
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

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
