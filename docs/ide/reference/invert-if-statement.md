---
title: Inverter instrução if
description: Saiba como usar o menu ações rápidas e refatoração para inverter uma instrução If ou if else sem alterar o significado do código.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cf4ad7c25030e4a331ee67f4957ddac59afdd966
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852226"
---
# <a name="invert-if-statement"></a>Inverter instrução if

Esta refatoração aplica-se a:

- C#
- Visual Basic

**O que:** Permite inverter `if` uma `if else` instrução or sem alterar o significado do código.

**Quando:** Quando você tem uma `if` `if else` instrução ou que seria melhor entendida quando invertida.

**Por que:** Inverter `if` uma `if else` instrução or manualmente pode levar muito mais tempo e possivelmente introduzir erros. Essa correção de código ajuda você a fazer a refatoração automaticamente.

## <a name="invert-if-statement-refactoring"></a>Refatoração de inverter instrução if

1. Coloque o cursor em uma instrução `if` ou `if else`.

    ![Inverter if else](media/invert-if.png)

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

    ![Correção para inverter código if else](media/invert-if-codefix.png)

3. Selecione **Inverter if**.

    ![Inverter o resultado de if else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
