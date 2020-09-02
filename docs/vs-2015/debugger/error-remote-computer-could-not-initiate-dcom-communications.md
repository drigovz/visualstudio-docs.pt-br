---
title: 'Erro: o computador remoto não pôde iniciar as comunicações DCOM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8ddec2bdec09da1f1175b59c94db31841a1453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697333"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Erro: o computador remoto não conseguiu iniciar a comunicação DCOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um erro DCOM ocorreu quando o computador remoto tentou se comunicar com o computador local. O computador local é o computador que está  
  
 executando o Visual Studio. Esse erro pode ocorrer por várias razões:  
  
- O computador local tem um firewall habilitado.  
  
- A autenticação do Windows do computador remoto para o computador local não está funcionando.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Se o computador local tiver o Firewall do Windows habilitado, consulte [Configurar o ferramentas remotas no dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) para obter instruções sobre como configurar o firewall para depuração local.  
  
2. Teste a autenticação do Windows tentando abrir um compartilhamento de arquivos no computador local do servidor remoto.  
  
3. Para restaurar a autenticação do Windows, tente reiniciar os dois computadores. Examine os logs de eventos nos computadores local e remoto para encontrar erros de Kerberos e entre em contato com os administradores de domínio para problemas conhecidos.  
  
## <a name="see-also"></a>Consulte Também  
 [Configurar as ferramentas remotas no dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
