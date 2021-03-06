---
title: Exibição de Funções – Dados de Amostragem | Microsoft Docs
description: Leia sobre a exibição de relatório do Functions para o método de perfil de amostragem, que lista as funções que foram amostradas durante a execução da criação de perfil.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 82b48689b6348c7d003f5418224260b7939e907a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907360"
---
# <a name="functions-view---sampling-data"></a>Exibição Funções – dados de amostragem
O modo de exibição de relatório de Funções do método de perfil de amostragem lista as funções que foram amostradas durante a criação de perfil.

> [!NOTE]
> Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

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
|**Amostras Inclusivas**|O número total de amostras que foram coletadas quando a função estava em execução, ou seja, o número de amostras que foram coletadas quando a função estava na pilha de chamadas. O número inclui amostras que foram coletadas quando as funções que foram chamadas por esta função estavam em execução.|
|**% de Amostras Inclusivas**|O percentual de todas as amostras na execução de criação de perfil que eram amostras inclusivas dessa função.|
|**Amostras Exclusivas**|O número total de amostras que foram coletadas quando o código no corpo da função estava em execução, ou seja, quando a função estava no topo na pilha de chamadas. Amostras que foram coletadas em funções que foram chamadas pela função não incluídas.|
|**% de Amostras Exclusivas**|O percentual de todas as amostras na execução de criação de perfil que eram amostras exclusivas dessa função.|

## <a name="see-also"></a>Confira também
- [Como: Personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md)
- [Exibição de funções – instrumentação](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Exibição de funções – amostragem](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Exibição de funções](../profiling/functions-view-instrumentation-data.md)
