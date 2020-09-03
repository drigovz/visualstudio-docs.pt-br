---
title: Ocorreu um erro de DCOM durante a tentativa de contatar o computador remoto. O acesso foi negado. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0157b1ade2c38a2c10920b9674d7c9a58ac036b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156527"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Ocorreu um erro de DCOM durante a tentativa de contatar o computador remoto. O acesso foi negado.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A depuração remota usa DCOM para se comunicar entre os computadores locais e remotos nas seguintes situações:  
  
- O depurador é definido como **modo de compatibilidade nativo** ou o **modo de compatibilidade gerenciado** é verificado na página **ferramentas/opções/depuração**  
  
- Você está depurando o código C++ (C++/CLI) gerenciado.  
  
- No Visual Studio 2013, quando **habilitar a opção Editar e continuar nativo** é marcado na página **ferramentas/opções/depuração**  
  
- Alguns cenários de depuração de terceiros  
  
  Esse erro ocorre quando o processo do Visual Studio não puder se autenticar (ou as credenciais fornecidas forem julgadas insuficientes) para o processo remoto do depurador sobre DCOM. Uma ou mais das seguintes alternativas podem resolver o problema:  
  
- Desative o modo de  **compatibilidade nativa** e o **modo de compatibilidade gerenciado**.  
  
- Em Visual Studio 2013, desative **Habilitar edição e continuar nativo**.  
  
- Reinicializar ambos os computadores.  
  
- Se a depuração remota exigir a inserção de credenciais, verifique a opção para salvar as credenciais.  
  
## <a name="see-also"></a>Consulte Também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)
