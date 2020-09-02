---
title: Mensagens de diagnóstico no Janela de Saída | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60f8da2430e1c84af3c26be31c6de561291c8c6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695290"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Mensagens de diagnóstico na janela Saída
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode gravar as mensagens de tempo de execução na janela Saída usando a classe de Depuração ou a classe de Rastreamento, que fazem parte da biblioteca de classes <xref:System.Diagnostics>. Use a classe de Depuração se você emitir uma saída apenas na versão de Depuração do programa. Use a classe de Rastreamento se você quiser uma saída nas versões de Depuração e de Inicialização.  
  
## <a name="output-methods"></a>Métodos de saída  
 As classes <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> fornecem os seguintes métodos de saída:  
  
- Vários métodos `Write`, os quais geram informações sem interromper a execução. Esses métodos substituem o método `Debug.Print` usado em versões anteriores do Visual Basic.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> e <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> os métodos, que interrompem a execução e geram informações se uma condição especificada falhar. Por padrão, o método `Assert` exibe informações em uma caixa de diálogo. Para obter mais informações, confira [Asserções em código gerenciado](../debugger/assertions-in-managed-code.md).  
  
- Os métodos <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, que sempre interrompem informações de execução e de saída. Por padrão, os métodos `Fail` exibem informações em uma caixa de diálogo.  
  
  Além de programar de seu aplicativo, a janela **saída** pode exibir as informações sobre:  
  
- Módulos que o depurador carregou ou descarregou.  
  
- Exceções lançadas.  
  
- Processos encerrados.  
  
- Threads encerrados.  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Janela Saída](../ide/reference/output-window.md)   
 [Rastreamento e instrumentação de aplicativos](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Introdução à instrumentação e ao rastreamento](https://msdn.microsoft.com/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [Tipos de projeto C#, F # e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)
