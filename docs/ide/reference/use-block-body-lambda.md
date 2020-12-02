---
title: Usar uma expressão de lambda ou o corpo do bloco
description: Saiba como usar o menu ações rápidas e refatoração para refatorar uma expressão lambda para usar um corpo de expressão ou um corpo de bloco.
ms.custom: SEO-VS-2020
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 505a76a2300f2e3ddb9c1513ee64c2a17abb10ab
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480168"
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