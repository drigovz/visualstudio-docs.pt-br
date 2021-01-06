---
title: Depurar o método OnStart | Microsoft Docs
description: Saiba como depurar o método OnStart de um serviço do Windows no Visual Studio — iniciando o depurador de dentro do método.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 488fe471552256e8fad62bb6f831448811ca343f
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903136"
---
# <a name="how-to-debug-the-onstart-method"></a>Como depurar o método OnStart
Você pode depurar um serviço do Windows iniciando o serviço e anexando o depurador ao processo do serviço. Para obter mais informações, confira [Como depurar aplicativos de Serviço Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). No entanto, para depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> método de um serviço do Windows, você deve iniciar o depurador de dentro do método.

1. Adicione uma chamada para <xref:System.Diagnostics.Debugger.Launch%2A> no início do `OnStart()` método.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Inicie o serviço (você pode usá `net start` -lo ou iniciá-lo na janela **Serviços** ).

    Você deverá ver uma caixa de diálogo semelhante à seguinte:

    ![Captura de tela de uma caixa de diálogo do depurador just-in-time do Visual Studio que mostra uma exceção de .NET Framework sem tratamento ocorrida no WindowsService-Asis.exe.](../debugger/media/onstartdebug.png)

3. Selecione **Sim, depurar \<service name> .**

4. Na janela do depurador just-in-time, selecione a versão do Visual Studio que você deseja usar para depuração.

    ![Captura de tela de uma janela do depurador just-in-time do Visual Studio com ' nova instância do Microsoft Visual Studio 2015 ' selecionada na lista de possíveis depuradores.](../debugger/media/justintimedebugger.png)

5. Uma nova instância do Visual Studio é iniciada e a execução é interrompida no `Debugger.Launch()` método.

## <a name="see-also"></a>Veja também
- [Segurança do depurador](../debugger/debugger-security.md)
- [Depurando código gerenciado](../debugger/debugging-managed-code.md)
