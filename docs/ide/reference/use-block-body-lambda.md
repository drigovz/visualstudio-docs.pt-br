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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531913"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Use o corpo da expressão ou o corpo do bloco para expressões lambda

Esta refatoração aplica-se a:

- C#

**O que:** Permite refatorar uma expressão lambda para usar um corpo de expressão ou um corpo de bloco.

**Quando:** Você prefere expressões lambda para usar um corpo de expressão ou um corpo de bloco.

**Por que:** Expressões lambda podem ser Refatorada para melhorar a legibilidade de acordo com a preferência do usuário.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refatoração do corpo do bloco ou do corpo da expressão lambda

1. Coloque o cursor à direita de um operador lambda.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

  ![Usar uma expressão de lambda/o corpo do bloco](media/block-body-lambda.png)

3. Selecione **Usar corpo do bloco para expressões lambda** ou **Usar corpo da expressão para expressões lambda**.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)