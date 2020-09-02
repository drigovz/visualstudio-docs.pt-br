---
title: Exibição tempo de vida do objeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef216c1220cbfda37da579d3ea2dfdd32837ab75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195562"
---
# <a name="object-lifetime-view"></a>Exibição do tempo de vida do objeto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição Tempo de Vida do Objeto está disponível quando **Também coletar dados de tempo de vida do objeto .NET** está marcada nas páginas de propriedades da Sessão de Desempenho.  
  
 O coletor de lixo do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] gerencia a alocação e liberação de memória para seu aplicativo. Para otimizar o desempenho do coletor de lixo, o heap gerenciado é dividido em três gerações: 0, 1 e 2. O coletor de lixo do runtime armazena novos objetos na geração 0. Os objetos que sobrevivem as coletas são promovidos e armazenados para as gerações 1 e 2.  
  
 O coletor de lixo recupera memória, desalocando uma geração inteira de objetos. Para objetos que foram criados pelo aplicativo com perfil criado, a exibição do Tempo de vida do objeto exibe o número e o tamanho dos objetos e a geração na qual eles são recuperados.  
  
## <a name="general"></a>Geral  
  
|Coluna|Descrição|  
|------------|-----------------|  
|**Nome da classe**|O nome de classe do tipo alocado.|  
|**ID do Processo**|A ID de processo da execução de criação de perfil.|  
|**Nome do processo**|O nome do processo.|  
|**Nome do módulo**|O nome do módulo que contém a função.|  
|**Caminho do Módulo**|O demarcador do módulo que contém a função.|  
  
## <a name="instance-data"></a>Dados de Instância  
 Dados de instância indicam o número de objetos do tipo que foram criados na execução de criação de perfil e a geração na qual os objetos foram desalocados pelo coletor de lixo.  
  
|Coluna|Descrição|  
|------------|-----------------|  
|**Instâncias**|O número de alocações de objetos desse tipo.|  
|**% Total de Instâncias**|O percentual do número total de alocações feitas na execução da criação de perfil.|  
|**Instâncias de Ger 0 Coletadas**|O número de instâncias do tipo que foram desalocadas na geração 0 do algoritmo de coleta de lixo.|  
|**Instâncias de Ger 1 Coletadas**|O número de instâncias do tipo que foram desalocadas na geração 1 do algoritmo de coleta de lixo.|  
|**Instâncias de Ger 2 Coletadas**|O número de instâncias do tipo que foram desalocadas na geração 2 do algoritmo de coleta de lixo.|  
|**Instâncias Ativas ao Final**|O número de instâncias do tipo que não foram desalocadas até o final da execução de criação de perfil.|  
  
## <a name="size-byte-data"></a>Dados de Tamanho (Byte)  
 Dados de tamanho (byte) indicam o tamanho de objetos do tipo que foram criados na execução de criação de perfil e a quantidade de memória que foi recuperada em cada geração na qual os objetos foram desalocados.  
  
|Coluna|Descrição|  
|------------|-----------------|  
|**Total de Bytes Alocados**|O número total de bytes para todas as instâncias do tipo.|  
|**% Total de Bytes**|O percentual do número total de bytes alocados na execução de criação que foram alocados para as instâncias desse tipo.|  
|**Bytes de Ger 0 Coletados**|O tamanho das instâncias do tipo que foram desalocadas na geração 0 do algoritmo de coleta de lixo.|  
|**Bytes de Ger 1 Coletados**|O tamanho das instâncias do tipo que foram desalocadas na geração 1 do algoritmo de coleta de lixo.|  
|**Bytes de Ger 2 Coletados**|O tamanho das instâncias do tipo que foram desalocadas na geração 2 do algoritmo de coleta de lixo.|  
  
## <a name="large-object-heap-data"></a>Dados de Heap de Objetos Grandes  
 O alocador de memória .NET gerencia objetos muito grandes em um local separado de heap gerenciado padrão. Dados de heap de objeto grande indicam o número e tamanho dos objetos do tipo que foram gerenciados neste local.  
  
|Coluna|Descrição|  
|------------|-----------------|  
|**Instâncias de Heap de Objetos Grandes Coletados**|O número de instâncias desse tipo que estavam no heap de objeto grande e que foram coletadas na execução da criação de perfil.|  
|**Bytes de Heap de Objetos Grandes Coletados**|O tamanho, em bytes, das instâncias desse tipo que estavam no heap de objeto grande e que foram coletadas na execução da criação de perfil.|  
  
## <a name="see-also"></a>Consulte Também  
 [Exibições de dados de memória do .NET](../profiling/dotnet-memory-data-views.md)
