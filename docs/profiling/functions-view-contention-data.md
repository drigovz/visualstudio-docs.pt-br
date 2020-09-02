---
title: Exibição de Funções – Dados de Contenção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5874ffc7b4d304d1eaacd78032d657fe6ff31d94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74780046"
---
# <a name="functions-view---contention-data"></a>Exibição Funções – dados de contenção
A exibição de relatório de Funções de dados de contenção lista as funções na execução de criação de perfil que foram bloqueadas da execução durante o processo de criação de perfil.

 A tabela a seguir explica os valores que são exibidos na exibição de Funções de um arquivo de dados de criação de perfil que foi coletado usando o método de simultaneidade.

|Coluna|Descrição|
|------------|-----------------|
|**Tempo Bloqueado Exclusivo**|A quantidade de tempo durante a qual essa função foi impedida de executar o código no corpo da função. Não inclui o tempo bloqueado nas funções que foram chamadas pela função.|
|**% de Tempo Bloqueado Exclusivo**|O percentual de todo o tempo bloqueado na execução da criação de perfil que representou o tempo bloqueado exclusivo desta função.|
|**Contenções Exclusivas**|A quantidade de vezes que essa função foi impedida de executar o código no corpo da função. As contenções em funções chamadas pela função não são incluídas.|
|**% de Contenções Exclusivas**|O percentual de todas as contenções na execução de criação de perfil era de contenções exclusivas desta função.|
|**Endereço da função**|O endereço da função.|
|**Nome da função**|O nome totalmente qualificado da função.|
|**Tempo Bloqueado Inclusivo**|A hora em que essa função ou uma função que foi chamada por esta função foi impedida de executar.|
|**% de Tempo Bloqueado Inclusivo**|O percentual de todo o tempo bloqueado na execução da criação de perfil que representou o tempo bloqueado inclusivo desta função ou módulo.|
|**Contenções Inclusivas**|O número de vezes que essa função ou uma função que foi chamada por esta função foi impedida de executar.|
|**% de Contenções Inclusivas**|O percentual de todas as contenções na execução de criação de perfil que eram contenções inclusivas dessa função ou módulo.|
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|
|**Nome do módulo**|O nome do módulo que contém a função.|
|**Caminho do Módulo**|O demarcador do módulo que contém a função.|
|**ID do Processo**|A PID (ID do processo) do processo no qual a função estava sendo executada.|
|**Nome do processo**|O nome do processo.|
|**Arquivo de Origem**|O arquivo de origem que contém a definição dessa função.|

## <a name="see-also"></a>Confira também
- [Como: Personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md)
- [Exibição de funções](../profiling/functions-view.md)
- [Exibição de funções – instrumentação](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Exibição de funções – amostragem](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Exibição de funções](../profiling/functions-view-instrumentation-data.md)
- [Exibição de funções](../profiling/functions-view-sampling-data.md)
