---
title: Ocorreu um erro de DCOM durante a tentativa de contatar o computador remoto. O acesso foi negado. | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fa7aca2b86e8cc7c8d9cea4eba27b850d26bc13
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825641"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Ocorreu um erro de DCOM durante a tentativa de contatar o computador remoto. O acesso foi negado.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Depuração remota usa DCOM para se comunicar entre os computadores locais e remotos nas seguintes situações:  
  
- O depurador está definido como **modo de compatibilidade nativa** ou **modo de compatibilidade gerenciado** check-in a **Ferramentas / opções / depuração** página  
  
- Você está depurando C++ gerenciado (C + + / CLI) código.  
  
- No Visual Studio 2013, quando **habilitar nativo editar e continuar** check-in a **Ferramentas / opções / depuração** página  
  
- Alguns cenários de depuração de terceiros  
  
  Esse erro ocorre quando o processo do Visual Studio não puder se autenticar (ou as credenciais fornecidas forem julgadas insuficientes) para o processo remoto do depurador sobre DCOM. Uma ou mais das seguintes alternativas podem resolver o problema:  
  
- Desative **modo de compatibilidade nativa** e **modo de compatibilidade gerenciado**.  
  
- No Visual Studio 2013, desative **habilitar nativo editar e continuar**.  
  
- Reinicializar ambos os computadores.  
  
- Se a depuração remota exigir a inserção de credenciais, verifique a opção para salvar as credenciais.  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas e erros de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)



