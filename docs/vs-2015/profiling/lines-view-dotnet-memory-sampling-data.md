---
title: Exibição de Linhas – Dados de Amostragem de Memória do .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 251dc4279530c2d10ba8b404ee515824d0671037
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62579976"
---
# <a name="lines-view---net-memory-sampling-data"></a>Exibição de linhas – Dados de Amostragem de Memória do .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição de Linhas dos dados de criação de perfil de alocação de memória do .NET que usa o método de amostragem lista as instruções que alocaram memória durante o processo de criação de perfil. As colunas também incluem o tamanho e o número de alocações.  
  
 Em um arquivo de origem, uma instrução pode abranger mais de uma linha em um arquivo de origem, e uma única linha pode incluir mais de uma instrução.  
  
 Uma instrução é identificada pelo seguinte:  
  
- O arquivo de origem que contém a instrução da função.  
  
- A função que contém a instrução.  
  
- A linha de origem em que a instrução se inicia.  
  
- O caractere na linha de origem em que a instrução se inicia.  
  
- A linha de origem em que a instrução termina.  
  
- O caractere na linha de origem em que a instrução termina.  
  
  A coluna de Nome de Linha fornece uma concatenação classificável dos dados do identificador.  
  
  Por definição, uma instrução não chama outras funções. Portanto, apenas valores exclusivos são listados.  
  
|Column|Descrição|  
|------------|-----------------|  
|**ID do Processo**|A ID de processo (PID) da criação de perfil.|  
|**Nome do Processo**|O nome do processo.|  
|**Nome do Módulo**|O nome do módulo que contém a instrução.|  
|**Caminho do Módulo**|O caminho do módulo que contém a instrução.|  
|**Arquivo de Origem**|O arquivo de origem que contém a instrução.|  
|**Nome da Função**|O nome da função que contém a instrução.|  
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|  
|**Endereço da Função**|O endereço inicial da função.|  
|**Início da Linha de Origem**|O número de linha inicial no arquivo de origem em que a alocação ocorreu.|  
|**Final da Linha de Origem**|O número de linha final no arquivo de origem em que a alocação ocorreu.|  
|**Início do Caractere de Origem**|O deslocamento do caractere inicial na linha do arquivo de origem em que a alocação ocorreu.|  
|**Final do Caractere de Origem**|O deslocamento do caractere final na linha do arquivo de origem em que a alocação ocorreu.|  
|**Nome da Linha**|Um identificador gerado pelo criador de perfil da linha com a seguinte sintaxe: `Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number Start,Character Start`**]**|  
|**Alocações Exclusivas**|O número total de objetos que foram criados nessa linha.|  
|**% de Alocações Exclusivas**|O percentual de todos os objetos criados na criação de perfil que foram alocados nessa linha.|  
|**Bytes Exclusivos**|O percentual de todos os bytes de memória alocados na criação de perfil que foram alocados nessa linha.|  
|**% de Bytes Exclusivos**|O percentual de todos os bytes de memória alocados na criação de perfil que foram alocados nessa linha.|  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Linhas](../profiling/lines-view-sampling-data.md)
