---
title: Modo de Exibição de Módulos – Dados de Contenção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2de844867e9c0a8d95abdaa13f860a6487254bfe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780007"
---
# <a name="modules-view---contention-data"></a>Exibição Módulos – dados de contenção
O modo de exibição de módulos de dados de contenção exibe dados de simultaneidade agrupados pelos módulos que foram utilizados nos dados de criação de perfil. Cada módulo é a raiz de uma árvore hierárquica. As funções do módulo no qual os eventos de contenção ocorreram são listadas sob o nó do módulo.

 Se a função estava executando seu próprio código quando ocorreu um evento de contenção, ou seja, a função estava na parte superior da pilha de chamadas, as linhas de origem e os endereços de instrução que estavam em execução são listados sob o nó de função. Como os dados são coletados para uma linha de origem ou um ponteiro de instrução quando a linha ou a instrução está em execução, os valores exclusivos e inclusivos são sempre os mesmos dados de linha e dados de instrução.

 A tabela a seguir descreve os valores das colunas na exibição de módulos de dados de contenção.

|Coluna|Descrição|
|------------|-----------------|
|**Tempo Bloqueado Exclusivo**|-Para uma função, a hora em que essa função foi impedida de executar o código no corpo da função. Não inclui o tempo bloqueado nas funções que foram chamadas pela função.<br />– Para um módulo, a soma do tempo de bloqueio exclusivo das funções no módulo.<br />- Para uma linha ou uma instrução, a hora em que esta linha ou instrução foi impedida de executar.|
|**% de Tempo Bloqueado Exclusivo**|-Para uma função ou um módulo, a porcentagem de tempo bloqueado todos na criação de perfil que era o tempo bloqueado exclusivo dessa função ou módulo.<br />– Para uma linha ou instrução, o percentual de todo o tempo bloqueado na execução de criação de perfil em que essa linha ou instrução teve sua execução bloqueada.|
|**Contenções Exclusivas**|-Para uma função, o número de vezes que essa função foi impedida de executar o código no corpo da função. As contenções em funções chamadas pela função não são incluídas.<br />– Para um módulo, a soma das contenções exclusivas das funções no módulo.<br />-Para uma linha ou uma instrução, o número de vezes que essa linha ou instrução foi impedida de executar.|
|**% de Contenções Exclusivas**|– Para uma função ou um módulo, o percentual de todas as contenções na execução de criação de perfil que eram contenções exclusivas dessa função ou módulo.<br />-Em uma linha ou uma instrução, a porcentagem de todas as disputas na criação de perfil que foram contenções que bloqueou essa linha ou instrução de execução.|
|**Tempo Bloqueado Inclusivo**|-Para uma função, a hora em que essa função ou uma função que foi chamada por esta função foi impedida de executar.<br />-Para um módulo, a soma do tempo bloqueado na qual pelo menos uma função desse módulo foi na pilha.<br />- Para uma linha ou uma instrução, a hora em que esta linha ou instrução foi impedida de executar.|
|**% de Tempo Bloqueado Inclusivo**|- Para uma função ou um módulo, o percentual de todo o tempo bloqueado na execução da criação de perfil que representou o tempo bloqueado inclusivo dessa função ou módulo.<br />– Para uma linha ou uma instrução, o percentual de todo o tempo de bloqueio na execução do perfil no qual esta linha ou instrução estava em execução.|
|**Contenções Inclusivas**|-Para uma função, o número de vezes que essa função ou uma função que foi chamada por esta função foi impedida de executar.<br />-Para um módulo, o número de contenções na qual pelo menos uma função desse módulo foi na pilha.<br />-Para uma linha ou uma instrução, o número de vezes que essa linha ou instrução foi impedida de executar.|
|**% de Contenções Inclusivas**|– Para uma função ou um módulo, o percentual de todas as contenções na execução de criação de perfil que eram contenções inclusivas dessa função ou módulo.<br />– Para uma linha ou uma instrução, o percentual de todo o tempo de bloqueio na execução do perfil no qual esta linha ou instrução estava em execução.|
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|
|**Nome do módulo**|O nome do módulo que contém a função, linha ou ponteiro de instrução.|
|**Caminho do Módulo**|O caminho do módulo que contém o módulo, função, linha ou ponteiro de instrução.|
|**Nome**|O nome do módulo ou da função.|
|**ID do Processo**|A ID de processo (PID) da criação de perfil.|
|**Nome do processo**|O nome do processo.|
|**Arquivo de origem**|O arquivo de origem que contém a definição dessa função.|

## <a name="see-also"></a>Confira também
- [Como: Personalizar colunas de exibição de relatórios](../profiling/how-to-customize-report-view-columns.md)
- [Exibição Módulos](../profiling/modules-view.md)
- [Exibição Módulos – instrumentação](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Exibição de módulos - amostragem](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Exibição Módulos](../profiling/modules-view-instrumentation-data.md)
- [Exibição Módulos](../profiling/modules-view-sampling-data.md)
