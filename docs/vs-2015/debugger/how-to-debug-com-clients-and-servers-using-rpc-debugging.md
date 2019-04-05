---
title: 'Como: Depurar clientes e servidores usando a depuração RPC COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1235abfc6e8a2c384b02fd1d48a859063c058d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924027"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Como: Depurar clientes e servidores COM usando a depuração RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar a depuração de chamada de procedimento remoto (RPC) para depurar aplicativos cliente/servidor COM. Você deve habilitar a depuração de RPC para usá-lo. Com a depuração de RPC habilitada, quando você entrar na chamada do servidor do cliente, o depurador anexará ao servidor e permitirá depurar o código. Quando o depurador for anexado, você poderá usar todos os recursos do depurador com o cliente e os processos do servidor.  
  
### <a name="to-enable-rpc-debugging"></a>Para habilitar a depuração de RPC  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  Na caixa de diálogo **Opções**, clique na pasta **Depuração**.  
  
3.  Clique na página **Nativa**.  
  
4.  Marque a caixa de seleção **Depuração RPC**.  
  
    > [!NOTE]
    >  Para depurar chamadas de RPC, você deve ter privilégios de Administrador ou Usuário avançado.  
  
    > [!NOTE]
    >  A entrada de RPC em um servidor remoto que executa o Microsoft Windows Vista só funcionará se um depurador nativo for anexado ao servidor remoto. Caso contrário, a chamada de RPC apresentará falha sem uma mensagem de erro. De outro modo, a chamada de RPC será concluída, mas a depuração da chamada de RPC não funcionará.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração de servidor e contêiner COM](../debugger/com-server-and-container-debugging.md)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)
