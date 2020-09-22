---
title: Criar um relatório ETW das Ferramentas de Criação de Perfil | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 13de203a6a9082b33f5d68f8b4e2fbdc6f0e14b3
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851184"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Como criar um relatório ETW das ferramentas de criação de perfil
O Relatório de Rastreamento de Eventos para Windows (ETW) lista os eventos ETW que são registrados em uma sessão de desempenho de Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Os dados ETW são coletados em um binário (.* ETL*). Para obter mais informações sobre esse relatório, consulte [relatório de ETW (rastreamento de eventos para Windows)](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> Não é possível exibir relatórios ETW na interface para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Para obter informações sobre como coletar dados do ETW usando a interface do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , consulte [como coletar dados do ETW (rastreamento de eventos para Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Para obter informações sobre como coletar dados de ETW de um prompt de comando, consulte [VSPerfCmd](../profiling/vsperfcmd.md) e [Eventos](../profiling/events-vsperfcmd.md).

  O relatório de ETW é gerado usando o comando **VSReport/summary:etw**. Dos. o *ETL* que contém os dados do ETW deve estar no mesmo diretório que os dados de criação de perfil (.* VSP* ou. *vsps*) Grupo. Por padrão, o relatório é gerado como um valor separado por vírgulas (.* CSV*). Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Para criar um relatório ETW

- Em uma janela de **Prompt de Comando**, digite a seguinte linha de comando:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |Item|Descrição|
    |-|-|
    |*ToolsPath*|O caminho do utilitário de Ferramentas de Criação de Perfil. Para saber mais, confira [Especificar o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Os dados de criação de perfil (.* VSP* ou. *vsps*) Grupo. Caminhos completos e parciais são aceitos.|
    |Xml|Gera um relatório que é formatado em XML.|
