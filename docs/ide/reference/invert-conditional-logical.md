---
title: Inverter expressões condicionais e operações lógicas
description: Saiba como usar o menu ações rápidas e refatoração para inverter uma expressão condicional ou um operador AND/OR condicional.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 180e42d5399116df95289e4e5fd0aed1255bf3de
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617377"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Inverter expressões condicionais e operadores AND/OR condicionais

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O que:** Permite inverter uma expressão condicional ou um operador AND/OR condicional.

**Quando:** Você tem uma expressão condicional ou um operador condicional AND/OR que seria melhor compreendido se for invertido.

**Por que:** Inverter uma expressão ou condicional e/ou operador manualmente pode levar muito mais tempo e possivelmente introduzir erros. Essa correção de código ajuda você a fazer a refatoração automaticamente.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Refatoração de inverter expressões condicionais e operadores AND/OR condicionais

1. Coloque o cursor em uma expressão condicional ou um operador AND/OR condicional.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Inverter condicional** ou **Substitua '&&' por '||'**

    ![Captura de tela da opção Inverter condicional.](media/invert-conditional.png)

    ![Captura de tela da && substituir por | | Option.](media/invert-logical-operator.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
