---
title: Exibição de chamador-computador chamado – Dados de amostragem | Microsoft Docs
description: Leia como o modo de exibição chamador/receptor exibe informações de criação de perfil para uma função selecionada e suas funções pai e filho no Gerenciador de Desempenho.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 376475d2a392b86b14a73ba45c5669eaaf338898
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886399"
---
# <a name="callercallee-view---sampling-data"></a>Exibição do chamador/receptor – dados de amostragem
A exibição de Chamador/Computador Chamado exibe informações de perfil para uma função selecionada e suas funções pai e filho. A exibição de Chamador/Computador Chamado contém três grades.

 **Função atual** é exibida na grade intermediária e mostra informações de criação de perfil para a função selecionada. Os valores incluem todas as chamadas amostradas para a função.

 **Funções que chamaram a função atual** é exibido na grade superior e mostra as contribuições individuais das funções de chamador (pai) para os valores da função selecionada (atual).

 **Funções que foram chamadas pela função atual** são exibidas na grade inferior e mostram informações de criação de perfil para as funções do computador chamado (filho) da função selecionada quando a função filho foi chamada pela função atual.

> [!NOTE]
> Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Coluna|Descrição|
|------------|-----------------|
|**ID do Processo**|A ID de processo (PID) da criação de perfil.|
|**Nome do processo**|O nome do processo.|
|**Nome do módulo**|O nome do módulo que contém a função.|
|**Caminho do Módulo**|O demarcador do módulo que contém a função.|
|**Arquivo de Origem**|O arquivo de origem que contém a definição dessa função.|
|**Nome da função**|O nome totalmente qualificado da função.|
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|
|**Endereço da função**|O endereço da função.|
|**Tipo**|O contexto da função:<br /><br /> -   **0** – a função atual<br />-   **1** – uma função que chama a função atual<br />-   **2** – uma função que é chamada pela função atual|
|**Nome da Função Raiz**|Nome da função atual.|
|**Amostras Inclusivas**|–   Para a função atual, o número de amostras que foram coletadas, embora essa função ou uma de suas funções filho estivesse em execução.<br />–   Para uma função do chamador, o número de amostras inclusivas da função atual que foram coletadas quando essa função chamou a função atual.<br />–   Para uma função do computador chamado, o número de amostras inclusivas dessa função que foram coletadas quando a função atual chamou essa função.|
|**% de Amostras Inclusivas**|O percentual de todas as amostras na execução de criação de perfil que eram amostras inclusivas dessa função.|
|**Amostras Exclusivas**|–   Para a função atual, o número de amostras na execução de criação de perfil que foram coletadas quando essa função estava diretamente em execução; ou seja, quando essa função estava na parte superior da pilha de chamadas. Amostras coletadas quando funções filho dessa função estão em execução não são contadas em contagens exclusivas.<br />–   Para uma função do chamador, o número de amostras exclusivas da função atual que foram coletadas quando essa função chamou a função atual.<br />–   Para uma função do computador chamado, o número de amostras exclusivas desta função que foram coletadas quando a função atual chamou essa função.|
|**% de Amostras Exclusivas**|O percentual de todas as amostras na execução de criação de perfil que eram amostras exclusivas dessa função.|

## <a name="see-also"></a>Confira também
- [Exibição Caller/Callee-dados de amostragem de memória .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Exibição do chamador/receptor-dados de instrumentação de memória .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Exibição do chamador/receptor-dados de instrumentação](../profiling/caller-callee-view-instrumentation-data.md)
