---
title: Inverter instrução if
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a0419100cbc5fcd543eb250fa85cbfe2ebd1c97f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531582"
---
# <a name="invert-if-statement"></a>Inverter instrução if

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O que é isso?** Permite inverter `if` `if else` uma ou declaração sem alterar o significado do código.

**Quando:** Quando você `if` tem `if else` uma ou declaração que seria melhor compreendida quando invertida.

**Por que:** Inverter `if` `if else` uma ou declaração manualmente pode levar muito mais tempo e possivelmente introduzir erros. Essa correção de código ajuda você a fazer a refatoração automaticamente.

## <a name="invert-if-statement-refactoring"></a>Refatoração de inverter instrução if

1. Coloque o cursor em uma instrução `if` ou `if else`.

    ![Inverter if else](media/invert-if.png)

2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

    ![Correção para inverter código if else](media/invert-if-codefix.png)

3. Selecione **Inverter if**.

    ![Inverter o resultado de if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
