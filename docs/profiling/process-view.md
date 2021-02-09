---
title: Exibição de processo | Microsoft Docs
description: Saiba como o modo de exibição de processo exibe dados de criação de perfil para os processos e threads que foram executados durante a execução da criação de perfil.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bc1f30fa815030204b5f2d306151fe815ed819f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910699"
---
# <a name="process-view"></a>Exibição de processo
A exibição do processo exibe dados de criação de perfil para os processos e threads executados durante o processo de criação de perfil.

 Os processos são listados por nome. Os threads são listados como nós filhos do processo que os criou. Os threads são nomeados pela função que iniciou o thread ou pelo rótulo **[ntdll.dll]** quando não há símbolos disponíveis.

 Clique com o botão direito do mouse na exibição e, em seguida, selecione **Adicionar/Remover Colunas** para adicionar ou remover colunas. Ou clique no nome da coluna para classificar os dados. Para obter mais informações, consulte [como: Personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md).

 As colunas da exibição de processo são as mesmas usadas pelos gerados pelos métodos de amostragem e instrumentação e pelos dados que incluem dados de memória do .NET. A tabela a seguir descreve os valores da coluna.

|Coluna|Descrição|
|------------|-----------------|
|**ID exclusiva**|Um identificador gerado pelo criador de perfil que é exclusivo ao processo ou thread.|
|**ID**|O identificador do processo ou thread gerado pelo sistema.|
|**Nome**|O nome do processo ou thread.|
|**Hora de início**|O número de milissegundos ou ciclos de processador desde o início da criação de perfil até o início do processo ou thread.|
|**Hora de término**|O número de milissegundos ou ciclos de processador desde o início da criação de perfil até o fim do processo ou thread.|

## <a name="see-also"></a>Consulte também
- [Exibições de dados do método de amostragem](../profiling/profiler-sampling-method-data-views.md)
- [Exibições de dados do método de instrumentação](../profiling/instrumentation-method-data-views.md)
- [Exibições de dados de memória do .NET](../profiling/dotnet-memory-data-views.md)
