---
title: Usar uma expressão de lambda ou o corpo do bloco
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5c46506e81e5334efea9060e957269e92e9d49cc
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531913"
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
- [Dicas para desenvolvedores de .NET](../csharp-developer-productivity.md)