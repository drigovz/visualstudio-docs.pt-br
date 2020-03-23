---
title: Encapsular, recuar e alinhar refatoração
description: Saiba como encapsular e alinhar cadeias de chamadas de métodos.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d801f052cb02e6a5b53189eeae342b9015d30f9b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093879"
---
# <a name="wrap-indent-and-align-refactorings"></a>Encapsular, recuar e alinhar refatoração

## <a name="wrap-and-align-call-chains"></a>Encapsular e alinhar cadeias de chamadas

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que é isso?** Permite embrulhar e alinhar cadeias de chamadas de método.

**Quando:** Você tem uma longa cadeia que consiste em várias chamadas de método em uma declaração.

**Por que:** Ler uma longa lista é mais fácil quando eles são embrulhados ou recuados de acordo com a preferência do usuário.

### <a name="how-to"></a>Como fazer

1. Posicione o cursor em qualquer uma das cadeias de chamadas.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Encapsular cadeia de chamadas** ou **Encapsular e alinhar cadeia de chamadas** para aceitar a refatoração.

   ![Encapsular e alinhar cadeias de chamadas](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Encapsular, recuar e alinhar parâmetros ou argumentos

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que é isso?** Permite embrulhar, identificar e alinhar parâmetros ou argumentos.

**Quando:** Você tem uma declaração de método ou chamada que tem vários parâmetros ou argumentos.

**Por que:** Ler uma longa lista de parâmetros ou argumentos é mais fácil quando eles são embrulhados ou recuados de acordo com a preferência do usuário.

### <a name="how-to"></a>Como fazer

1. Coloque o cursor em uma lista de parâmetros.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Encapsular, recuar e alinhar parâmetros](media/wrap-parameters.png)

3. Selecione **Embrulhe todos os parâmetros** para aceitar a refatoração.

## <a name="wrap-binary-expressions"></a>Encapsular expressões binárias

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que é isso?** Permite embrulhar expressões binárias.

**Quando:** Você tem uma expressão binária.

**Por que:** Ler uma expressão binária é mais fácil quando é embrulhado à preferência do usuário.

### <a name="how-to"></a>Como fazer

1. Coloque o cursor na expressão binária.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **A expressão Wrap** para aceitar a refatoração.

   ![Encapsular e alinhar cadeias de chamadas](media/wrap-binary-expression.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
