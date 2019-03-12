---
title: Inverter expressões condicionais e operações lógicas
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
ms.openlocfilehash: a35f5949bee6cb3c4fbcbf9ba6a9b501d54b2014
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324581"
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
- [Dicas para desenvolvedores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
