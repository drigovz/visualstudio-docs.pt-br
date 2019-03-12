---
title: Inverter instrução if
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a6dd0a3ebdb41243734850cea4f4b43604ebb94b
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324661"
---
# <a name="invert-if-statement"></a>Inverter instrução if

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O quê:** Permite inverter uma instrução `if` ou `if else` sem alterar o significado do código.

**Quando:** Quando você tem uma instrução `if` ou `if else` que será melhor compreendida quando invertida.

**Por que:** A inversão manual de uma instrução `if` ou `if else` pode levar muito mais tempo e, possivelmente, introduzir erros. Essa correção de código ajuda você a fazer a refatoração automaticamente.

## <a name="invert-if-statement-refactoring"></a>Refatoração de inverter instrução if

1. Coloque o cursor em uma instrução `if` ou `if else`.

    ![Inverter if else](media/invert-if.png)

2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

    ![Correção de código de inverter if else](media/invert-if-codefix.png)

3. Selecione **Inverter if**.

    ![Inverter o resultado de if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
