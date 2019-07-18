---
title: QueryCounters | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdd2707a6af2b9d03e73c696884dc12413437b04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178278"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A opção **QueryCounters** lista os contadores de desempenho de CPU (hardware) que estão disponíveis no computador.  
  
 **QueryCounters** deve ser a única opção na linha de comando.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum  
  
## <a name="remarks"></a>Comentários  
 Quando você estiver usando o método de instrumentação, o criador de perfil pode coletar os valores de um ou mais contadores de desempenho de CPU em cada evento de coleta de dados. Quando você estiver usando o método de criação de perfil de amostragem, você pode especificar um evento de contador e o número de ocorrências de eventos a ser usado como o intervalo de amostragem.  
  
 Processadores diferentes expõem diferentes contadores de desempenho da CPU. O criador de perfil define um conjunto de contadores genéricos que pode ser usado em quase todos os processadores. A opção **QueryCounters** lista os nomes dos contadores genéricos tanto os nomes dos contadores que são específicos para o processador.  
  
## <a name="see-also"></a>Veja também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)
