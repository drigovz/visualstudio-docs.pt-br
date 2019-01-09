---
title: Desligamento| Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 435011200065f1f27ff54c14c57d71eb651fd8e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952067"
---
# <a name="shutdown"></a>Desligar
A opção **Desligamento** aguarda qualquer processo com perfil finalizar ou desanexar e, em seguida, desativa o criador de perfil e fecha o arquivo de dados de criação de perfil. A opção **desligamento** deve ser o último comando de criação de um perfil.  
  
 Se um parâmetro de tempo limite não for especificado, a opção **Desligamento** aguardará indefinidamente. Se um parâmetro de tempo limite for especificado, a opção retornará após o número especificado de segundos, sem desativar o criador de perfil ou fechar o arquivo de dados.  
  
 A opção **desligamento** deve ser a única opção especificada na linha de comando.  
  
## <a name="syntax"></a>Sintaxe  
  
```cmd  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Timeout`  
 -   (Opcional) Se especificado, a opção retorna após o número especificado de segundos sem desativar o criador de perfil ou fechar o arquivo de dados de criação de perfil.  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criar perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)