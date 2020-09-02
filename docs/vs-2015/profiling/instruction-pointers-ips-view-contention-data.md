---
title: Exibição de IPs (ponteiros de instrução) – Dados de contenção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b27b185e659fc3a1f0adca4379896543a1eb87ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187844"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Exibição de IPs (ponteiros de instrução) – Dados de contenção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O modo de exibição de IPs dos dados de contenção lista dados para as instruções de assembly cuja execução foi bloqueada na execução da criação de perfil.  
  
 A tabela a seguir explica os valores das colunas no modo de exibição de Ponteiros de Instrução.  
  
|Coluna|Descrição|  
|------------|-----------------|  
|**Tempo Bloqueado Exclusivo**|O tempo de bloqueio nesta função.|  
|**% de Tempo Bloqueado Exclusivo**|O percentual de tempo de bloqueio enquanto a instrução era executada.|  
|**Contenções Exclusivas**|O número de contenções que ocorreram enquanto a instrução era executada.|  
|**% de Contenções Exclusivas**|O percentual de todas as contenções da criação de perfil que ocorreram durante a execução da instrução.|  
|**Endereço da função**|O endereço de memória inicial da função no binário carregado.|  
|**Nome da função**|O nome da função que contém a instrução.|  
|**Endereço da Instrução**|O endereço de memória da instrução no binário carregado.|  
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|  
|**Nome do módulo**|O nome do módulo que contém a instrução.|  
|**Caminho do Módulo**|O caminho do módulo que contém a instrução.|  
|**ID do Processo**|A PID (ID do processo) do processo analisado.|  
|**Nome do processo**|O nome do processo.|  
|**Início do Caractere de Origem**|O deslocamento do caractere na linha do arquivo de origem em que esta instrução começa.|  
|**Final do Caractere de Origem**|O deslocamento do caractere na linha do arquivo de origem em que esta instrução termina.|  
|**Arquivo de Origem**|O arquivo de origem que contém a instrução.|  
|**Início da Linha de Origem**|O número de linha no arquivo de origem em que esta instrução começa.|  
|**Final da Linha de Origem**|O número de linha no arquivo de origem em que esta instrução termina.|  
  
## <a name="see-also"></a>Consulte Também  
 [Como: Personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md)   
 [Exibição de ponteiros de instrução (IPs)](../profiling/instruction-pointers-ips-view.md)   
 [Exibição de ponteiros de instrução (IPs)-amostragem](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Exibição de ponteiros de instrução (IPs)](../profiling/instruction-pointers-ips-view-sampling-data.md)
