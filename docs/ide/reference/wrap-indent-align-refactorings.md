---
title: Encapsular, recuar e alinhar refatoração
description: Saiba como encapsular e alinhar cadeias de chamadas de métodos.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7c218d914bc234533af674fc5d138a1c102d85c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836262"
---
# <a name="wrap-indent-and-align-refactorings"></a>Encapsular, recuar e alinhar refatoração

## <a name="wrap-and-align-call-chains"></a>Encapsular e alinhar cadeias de chamadas

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Permite encapsular e alinhar cadeias de chamadas de método.

**Quando:** Você tem uma cadeia longa que consiste em várias chamadas de método em uma instrução.

**Por que:** É mais fácil ler uma lista longa quando elas são encapsuladas ou recuadas de acordo com a preferência do usuário.

### <a name="how-to"></a>Como fazer

1. Posicione o cursor em qualquer uma das cadeias de chamadas.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Encapsular cadeia de chamadas** ou **Encapsular e alinhar cadeia de chamadas** para aceitar a refatoração.

   ![Screeenshot do menu ações rápidas e refatoração no Visual Studio com cadeia de chamadas do Warap selecionadas e alterações de código C# mostradas.](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Encapsular, recuar e alinhar parâmetros ou argumentos

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Permite encapsular, recuar e alinhar parâmetros ou argumentos.

**Quando:** Você tem uma declaração de método ou chamada que tem vários parâmetros ou argumentos.

**Por que:** Ler uma longa lista de parâmetros ou argumentos é mais fácil quando eles são encapsulados ou recuados de acordo com a preferência do usuário.

### <a name="how-to"></a>Como fazer

1. Coloque o cursor em uma lista de parâmetros.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Encapsular, recuar e alinhar parâmetros](media/wrap-parameters.png)

3. Selecione **encapsular todos os parâmetros** para aceitar a refatoração.

## <a name="wrap-binary-expressions"></a>Encapsular expressões binárias

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Permite encapsular expressões binárias.

**Quando:** Você tem uma expressão binária.

**Por que:** É mais fácil ler uma expressão binária quando ela é ajustada à preferência do usuário.

### <a name="how-to"></a>Como fazer

1. Coloque o cursor na expressão binária.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione a **expressão de encapsulamento** para aceitar a refatoração.

   ![Screeenshot do menu ações rápidas e refatoração no Visual Studio com a expressão Warap selecionada e as alterações de código em C# mostradas.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
