---
title: Enviar mensagens para a janela de saída | Microsoft Docs
description: Gravar mensagens de tempo de execução na janela de saída no Visual Studio usando a classe Debug ou a classe Trace, que fazem parte da biblioteca de classes System. Diagnostics.
ms.custom: SEO-VS-2020
ms.date: 11/08/2018
ms.topic: how-to
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b61d0c6bc89f8be2680930411e0b9109fdeec473
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872048"
---
# <a name="send-messages-to-the-output-window"></a>Enviar mensagens para a Janela de Saída

Você pode gravar mensagens de tempo de execução na janela de **saída** usando a <xref:System.Diagnostics.Debug> classe ou a <xref:System.Diagnostics.Trace> classe, que fazem parte da <xref:System.Diagnostics> biblioteca de classes. Use a <xref:System.Diagnostics.Debug> classe se você quiser apenas a saída na versão de *depuração* do seu programa. Use a <xref:System.Diagnostics.Trace> classe se você quiser a saída nas versões de *depuração* e de *lançamento* .

## <a name="output-methods"></a>Métodos de saída
 As classes <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> fornecem os seguintes métodos de saída:

- Vários métodos `Write`, os quais geram informações sem interromper a execução. Esses métodos substituem o método `Debug.Print` usado em versões anteriores do Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> e <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> os métodos, que interrompem a execução e as informações de saída se uma condição especificada falhar. Por padrão, o método `Assert` exibe informações em uma caixa de diálogo. Para obter mais informações, consulte [asserções em código gerenciado](../debugger/assertions-in-managed-code.md).

- Os <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> métodos e, que sempre quebram as informações de execução e de saída. Por padrão, os métodos `Fail` exibem informações em uma caixa de diálogo.

A janela **saída** também pode exibir informações sobre:

- Módulos que o depurador carregou ou descarregou.

- Exceções lançadas.

- Processos encerrados.

- Threads encerrados.

## <a name="see-also"></a>Confira também
- [Segurança do depurador](../debugger/debugger-security.md)
- [janela Saída](../ide/reference/output-window.md)
- [Rastrear e instrumentar aplicativos](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Tipos de projeto C#, F # e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Depuração de código gerenciado](../debugger/debugging-managed-code.md)
