---
title: 'Como: Depurar o método OnStart | Microsoft Docs'
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
ms.openlocfilehash: 2a527a103b72d0026a7732a53b45d03793769058
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078701"
---
# <a name="how-to-debug-the-onstart-method"></a>Como: Depurar o método OnStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode depurar um serviço Windows iniciando o serviço e anexando o depurador ao processo do serviço. Para obter mais informações, confira [Como: Depurar aplicativos do serviço Windows](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2). No entanto, para depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> método de um serviço do Windows, você deve iniciar o depurador de dentro do método.  
  
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
