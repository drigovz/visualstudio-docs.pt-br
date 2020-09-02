---
title: 'Como: depurar o método OnStart | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 391b906889dcbe422f7ec227b1d375be82e7ac91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700197"
---
# <a name="how-to-debug-the-onstart-method"></a>Como depurar o método OnStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode depurar um serviço do Windows iniciando o serviço e anexando o depurador ao processo do serviço. Para obter mais informações, confira [Como depurar aplicativos de Serviço Windows](https://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2). No entanto, para depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> método de um serviço do Windows, você deve iniciar o depurador de dentro do método.  
  
1. Adicione uma chamada para <xref:System.Diagnostics.Debugger.Launch%2A> no início do `OnStart()` método.  
  
    ```csharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2. Inicie o serviço (você pode usá `net start` -lo ou iniciá-lo na janela **Serviços** ).  
  
     Você deverá ver uma caixa de diálogo semelhante à seguinte:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3. Selecione **Sim, depurar \<service name> .**  
  
4. Na janela do depurador just-in-time, selecione a versão do Visual Studio que você deseja usar para depuração.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5. Uma nova instância do Visual Studio é iniciada e a execução é interrompida no `Debugger.Launch()` método.  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)
