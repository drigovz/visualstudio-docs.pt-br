---
title: Desligamento| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b9b8848399ea88b5f4ce7ebf30f970e2091e6406
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784593"
---
# <a name="shutdown"></a>Desligar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A opção **desligamento** aguarda qualquer processo com perfil finalizar ou desanexar e, em seguida, desativa o criador de perfil e fecha o arquivo de dados de criação de perfil. A opção **desligamento** deve ser o último comando de criação de um perfil.  
  
 Se um parâmetro de tempo limite não for especificado, a opção **desligamento** aguardará indefinidamente. Se um parâmetro de tempo limite é especificado, a opção retorna após o número especificado de segundos, sem desativar o criador de perfil ou fechar o arquivo de dados.  
  
 A opção **desligamento** deve ser a única opção especificada na linha de comando.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Timeout`  
 -   (Opcional) Se especificado, a opção retorna após o número especificado de segundos sem desativar o criador de perfil ou fechar o arquivo de dados de criação de perfil.  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)
