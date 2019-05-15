---
title: Inverter expressões condicionais e operações lógicas
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
ms.openlocfilehash: 3931ae53fc29b0ffd8b8b6e96951a0f4786ff756
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531685"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Inverter expressões condicionais e operadores AND/OR condicionais

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O quê:** Permite inverter uma expressão condicional ou um operador AND/OR condicional.

**Quando:** Você tem uma expressão condicional ou um operador AND/OR condicional que será melhor compreendido se invertido.

**Por que:** A inversão manual de uma expressão ou um operador AND/OR condicional pode levar muito mais tempo e, possivelmente, introduzir erros. Essa correção de código ajuda você a fazer a refatoração automaticamente.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Refatoração de inverter expressões condicionais e operadores AND/OR condicionais

1. Coloque o cursor em uma expressão condicional ou um operador AND/OR condicional.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Inverter condicional** ou **Substitua '&&' por '||'**

    ![Inverter condicional](media/invert-conditional.png)

    ![Inverter condicional](media/invert-logical-operator.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores de .NET](../csharp-developer-productivity.md)
