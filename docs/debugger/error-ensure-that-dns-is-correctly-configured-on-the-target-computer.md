---
title: 'Erro: Certifique-se de que o DNS esteja configurado corretamente no computador de destino | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb5d5091f38835134c8803f58962a250790b24c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996487"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Erro: Verifique se o DNS está configurado corretamente no computador de destino
Ao tentar fazer a depuração remota, você pode receber a seguinte mensagem de erro:  
  
```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Esse erro ocorre quando o computador de destino não pode resolver o nome do computador host do depurador do Visual Studio. Verifique as configurações DNS no computador de destino.  
  
- Para obter informações sobre como exibir a configuração DNS no Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 ou Windows Server 2008 R2, fazer isso: sobre o **iniciar** menu, escolha **ajuda e suporte** e, em seguida, pesquise **configurações de TCP/IP de alteração**.  
  
- Para obter mais informações, vá para o [site do Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) e pesquise **Alterar configurações de TCP/IP**.  
  
  Se você não conseguir resolver o problema de DNS, tente executar o Depurador Remoto em uma conta diferente. Esse erro ocorre somente quando você está executando o Depurador Remoto sob a conta Serviço de Rede ou Sistema Local. Se você executar o Depurador Remoto em outra conta, ele poderá usar a autenticação NTLM, que não exige DNS. . Para o procedimento, consulte [erro: O serviço do Depurador Remoto do Visual Studio no computador de destino não pode se conectar novamente a esse computador](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)
