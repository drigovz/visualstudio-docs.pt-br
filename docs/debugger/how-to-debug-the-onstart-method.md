---
title: 'Como: depurar o método OnStart | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cfd6153389bbfe9cbbd36f33f6a2e4384509297
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227055"
---
# <a name="how-to-debug-the-onstart-method"></a>Como depurar o método OnStart
Você pode depurar um serviço Windows iniciando o serviço e anexando o depurador ao processo do serviço. Para obter mais informações, confira [Como depurar aplicativos de Serviço Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). No entanto, para depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> método de um serviço do Windows, você deve iniciar o depurador de dentro do método.

1. Adicione uma chamada para <xref:System.Diagnostics.Debugger.Launch%2A> no início do `OnStart()`método.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Inicie o serviço (você pode usar `net start`, ou iniciá-lo na **Services** janela).

    Você deve ver uma caixa de diálogo semelhante à seguinte:

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Selecione **Sim, depurar \<nome do serviço >.**

4. Na janela do depurador Just-in-, selecione a versão do Visual Studio que você deseja usar para depuração.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Uma nova instância do Visual Studio ser iniciado e a execução é interrompida no `Debugger.Launch()` método.

## <a name="see-also"></a>Consulte também
[Segurança do depurador](../debugger/debugger-security.md)  
[Depurando código gerenciado](../debugger/debugging-managed-code.md)
