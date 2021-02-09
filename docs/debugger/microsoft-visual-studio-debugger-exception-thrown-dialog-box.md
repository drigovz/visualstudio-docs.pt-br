---
title: Caixa de diálogo depurador de Microsoft Visual Studio (exceção gerada) | Microsoft Docs
titleSuffix: ''
description: 'Saiba o que fazer quando ocorrer uma exceção que o programa precisa manipular. Você pode: 1) entrar no depurador; 2) continuar; ou 3) ignorar.'
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2982912a0bf165f25b7777311d6db9a1bbe01a8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930272"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Caixa de diálogo Depurador do Microsoft Visual Studio (exceção gerada)
Ocorreu uma exceção no seu programa. Esta caixa de diálogo relata o tipo de exceção lançada. Seu código precisa tratar essa exceção. Você pode escolher entre as seguintes opções para tratar a exceção:

 **Interromper** Permite que a execução quebre no depurador. O manipulador de exceção não será invocado antes da interrupção. Se você continuar a partir da interrupção, o manipulador de exceção será invocado.

 **Continuar** Permite que a execução Continue, dando ao manipulador de exceção uma chance de lidar com a exceção. Essa opção não está disponível para determinados tipos de exceções. **Continuar** permitirá que o aplicativo continue. Em um aplicativo nativo, ela fará com que a exceção seja relançada. Em um aplicativo gerenciado, ela fará com que o programa seja encerrado ou a exceção seja tratada por um aplicativo de hospedagem.

> [!NOTE]
> Você não pode continuar depois de uma exceção sem tratamento em código gerenciado. A escolha de **Continuar** depois de uma exceção sem tratamento no código gerenciado faz com que a depuração pare.

 **Ignorar** Permite que a execução continue sem invocar o manipulador de exceção. Como o manipulador de exceção não é invocado, isso poderá resultar em outras consequências, incluindo erros e exceções adicionais. Essa opção não está disponível para determinados tipos de exceções.

## <a name="see-also"></a>Confira também
- [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md)
- [Práticas recomendadas para exceções](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Tratamento de exceção](/cpp/extensions/exception-handling-cpp-component-extensions)