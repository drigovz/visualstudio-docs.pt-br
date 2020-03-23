---
title: Como criar um relatório ETW das ferramentas de criação de perfil | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce7b02be682d825205fc5fa50d07c1ca817a24d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776395"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Como criar um relatório ETW das ferramentas de criação de perfil
O Relatório de Rastreamento de Eventos para Windows (ETW) lista os eventos ETW que são registrados em uma sessão de desempenho de Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Os dados do ETW são coletados em um binário (.* etl*) arquivo. Para obter mais informações sobre este relatório, consulte [o relatório Event Tracing for Windows (ETW).](../profiling/event-tracing-for-windows-etw-report.md)

> [!NOTE]
> Não é possível exibir relatórios ETW na interface para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Para obter informações sobre como coletar dados do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ETW usando a interface para , consulte [Como coletar dados de Rastreamento de Eventos para Windows (ETW).](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

- Para obter informações sobre como coletar dados de ETW de um prompt de comando, consulte [VSPerfCmd](../profiling/vsperfcmd.md) e [Eventos](../profiling/events-vsperfcmd.md).

  O relatório de ETW é gerado usando o comando **VSReport/summary:etw**. O. *etl* que contém os dados do ETW devem estar no mesmo diretório que os dados de criação de perfil (.* vsp* ou . *vsps*) Arquivo. Por padrão, o relatório é gerado como um valor separado por comma (.* csv*) arquivo. Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Para criar um relatório ETW

- Em uma janela de **Prompt de Comando**, digite a seguinte linha de comando:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |||
    |-|-|
    |*ToolsPath*|O caminho do utilitário de Ferramentas de Criação de Perfil. Para saber mais, confira [Especificar o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Os dados de criação de perfil (.* vsp* ou . *vsps*) Arquivo. Caminhos completos e parciais são aceitos.|
    |Xml|Gera um relatório que é formatado em XML.|
