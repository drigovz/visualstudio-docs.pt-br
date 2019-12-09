---
title: Exibição de IPs (ponteiros de instrução) – Dados de contenção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f37fb451238ec7ce6f48d8a4d3b91efa9ce04db7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774306"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Exibição de IPs (ponteiros de instrução) – dados de contenção
O modo de exibição de IPs dos dados de contenção lista dados para as instruções de assembly cuja execução foi bloqueada na execução da criação de perfil.

 A tabela a seguir explica os valores das colunas no modo de exibição de Ponteiros de Instrução.

|Column|Descrição|
|------------|-----------------|
|**Tempo Bloqueado Exclusivo**|O tempo de bloqueio nesta função.|
|**% de Tempo Bloqueado Exclusivo**|O percentual de tempo de bloqueio enquanto a instrução era executada.|
|**Contenções Exclusivas**|O número de contenções que ocorreram enquanto a instrução era executada.|
|**% de Contenções Exclusivas**|O percentual de todas as contenções da criação de perfil que ocorreram durante a execução da instrução.|
|**Endereço da Função**|O endereço de memória inicial da função no binário carregado.|
|**Nome da Função**|O nome da função que contém a instrução.|
|**Endereço da Instrução**|O endereço de memória da instrução no binário carregado.|
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|
|**Nome do Módulo**|O nome do módulo que contém a instrução.|
|**Caminho do Módulo**|O caminho do módulo que contém a instrução.|
|**ID do Processo**|A PID (ID do processo) do processo analisado.|
|**Nome do Processo**|O nome do processo.|
|**Início do Caractere de Origem**|O deslocamento do caractere na linha do arquivo de origem em que esta instrução começa.|
|**Final do Caractere de Origem**|O deslocamento do caractere na linha do arquivo de origem em que esta instrução termina.|
|**Arquivo de Origem**|O arquivo de origem que contém a instrução.|
|**Início da Linha de Origem**|O número de linha no arquivo de origem em que esta instrução começa.|
|**Final da Linha de Origem**|O número de linha no arquivo de origem em que esta instrução termina.|

## <a name="see-also"></a>Consulte também
- [Como: Personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md)
- [Exibição de IPs (ponteiros de instrução)](../profiling/instruction-pointers-ips-view.md)
- [Exibição de IPs (ponteiros de instrução) – amostragem](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Exibição de IPs (ponteiros de instrução)](../profiling/instruction-pointers-ips-view-sampling-data.md)
