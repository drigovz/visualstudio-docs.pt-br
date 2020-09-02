---
title: Exibição de Processo– Dados de Contenção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e43541ddb75b067faa23437d315ce5f239256b1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180228"
---
# <a name="process-view---contention-data"></a>Exibição de processo – dados de contenção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição Processo exibe dados de contenção para os processos e threads que foram executados durante o processo de criação de perfil.  
  
 Se os símbolos estiverem disponíveis, os processos serão listados por nome. Se os símbolos não estiverem disponíveis, os processos serão listados por seu endereço de memória em formato hexadecimal. Threads são listados como filhos do processo que os criou.  
  
 A tabela a seguir explica os valores das colunas na tabela de exibição Processo.  
  
|Coluna|Descrição|  
|------------|-----------------|  
|**Hora de início**|O número de milissegundos ou ciclos de processador desde o início da criação de perfil até o início do processo ou thread.|  
|**Tempo bloqueado**|O tempo total durante o qual a execução das funções do processo ou thread foi bloqueada.|  
|**% de Tempo Bloqueado**|O percentual do tempo de vida do processo ou thread no qual a execução de funções do processo ou thread foi bloqueada.|  
|**Contenções**|O número de vezes em que a execução das funções do processo ou thread foi bloqueada.|  
|**% de contenções**|O percentual de todas as contenções na criação de perfil que eram contenções do processo ou thread.|  
|**Hora de término**|O número de milissegundos ou ciclos de processador desde o início da criação de perfil até o fim do processo ou thread.|  
|**ID**|O identificador do processo ou thread gerado pelo sistema.|  
|**Tempo de vida**|O número de milissegundos ou ciclos de processador desde o início do processo ou thread até seu fim, thread ou o fim da criação de perfil.|  
|**Tipo**|O tipo de linha, processo ou thread.<br /><br /> Somente em relatórios de linha de comando do **VSReport** . Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nome**|O nome do processo ou thread.|  
|**ID exclusiva**|Um identificador gerado pelo criador de perfil que é exclusivo ao processo ou thread.|  
  
## <a name="see-also"></a>Consulte Também  
 [Como: Personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md)   
 [Exibição de processo](../profiling/process-view.md)
