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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531913"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Use o corpo da expressão ou o corpo do bloco para expressões lambda

Esta refatoração aplica-se a:

- C#

**O que é isso?** Permite que você refatorie uma expressão lambda para usar um corpo de expressão ou um corpo de bloqueio.

**Quando:** Você prefere expressões lambda para usar um corpo de expressão ou um corpo de bloco.

**Por que:** Expressões Lambda podem ser refatoradas para melhorar a legibilidade de acordo com a preferência do usuário.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refatoração do corpo do bloco ou do corpo da expressão lambda

1. Coloque o cursor à direita de um operador lambda.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

  ![Usar uma expressão de lambda/o corpo do bloco](media/block-body-lambda.png)

3. Selecione **Usar corpo do bloco para expressões lambda** ou **Usar corpo da expressão para expressões lambda**.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)