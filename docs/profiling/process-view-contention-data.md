---
title: Exibição de Processo– Dados de Contenção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79f9330733a0d32faeb9980813f170f52a6f7121
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965623"
---
# <a name="process-view---contention-data"></a>Exibição Processo – dados de contenção
A exibição Processo exibe dados de contenção para os processos e threads que foram executados durante o processo de criação de perfil.

 Se os símbolos estiverem disponíveis, os processos serão listados por nome. Se os símbolos não estiverem disponíveis, os processos serão listados por seu endereço de memória em formato hexadecimal. Threads são listados como filhos do processo que os criou.

 A tabela a seguir explica os valores das colunas na tabela de exibição Processo.

|Column|Descrição|
|------------|-----------------|
|**Hora de início**|O número de milissegundos ou ciclos de processador desde o início da criação de perfil até o início do processo ou thread.|
|**Tempo bloqueado**|O tempo total durante o qual a execução das funções do processo ou thread foi bloqueada.|
|**% de Tempo Bloqueado**|O percentual do tempo de vida do processo ou thread no qual a execução de funções do processo ou thread foi bloqueada.|
|**Contenções**|O número de vezes em que a execução das funções do processo ou thread foi bloqueada.|
|**% de contenções**|O percentual de todas as contenções na criação de perfil que eram contenções do processo ou thread.|
|**Hora de término**|O número de milissegundos ou ciclos de processador desde o início da criação de perfil até o fim do processo ou thread.|
|**ID**|O identificador do processo ou thread gerado pelo sistema.|
|**Tempo de vida**|O número de milissegundos ou ciclos de processador desde o início do processo ou thread até seu fim, thread ou o fim da criação de perfil.|
|**Tipo**|O tipo de linha, processo ou thread.<br /><br /> Somente em relatórios de linha de comando **VSReport**. Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).|
|**Nome**|O nome do processo ou thread.|
|**ID exclusiva**|Um identificador gerado pelo criador de perfil que é exclusivo ao processo ou thread.|

## <a name="see-also"></a>Consulte também
- [Como: Personalizar as colunas da Exibição de Relatório](../profiling/how-to-customize-report-view-columns.md)
- [Exibição de Processo](../profiling/process-view.md)