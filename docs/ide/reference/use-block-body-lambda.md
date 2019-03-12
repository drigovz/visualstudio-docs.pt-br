---
title: Usar uma expressão de lambda ou o corpo do bloco
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 01ea32ffe978d7b1544597857187f00bec9c3467
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324761"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Use o corpo da expressão ou o corpo do bloco para expressões lambda

Esta refatoração aplica-se a:

- C#

**O quê:** Permite refatorar uma expressão lambda para usar um corpo da expressão ou um corpo do bloco.

**Quando:** Você prefere que as expressões lambda usem um corpo da expressão ou um corpo do bloco. 

**Por que:** As expressões lambda podem ser refatoradas para melhorar a legibilidade de acordo com a preferência do usuário.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refatoração do corpo do bloco ou do corpo da expressão lambda

1. Coloque o cursor à direita de um operador lambda.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

  ![Usar uma expressão de lambda/o corpo do bloco](media/block-body-lambda.png)

3. Selecione **Usar corpo do bloco para expressões lambda** ou **Usar corpo da expressão para expressões lambda**.

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)