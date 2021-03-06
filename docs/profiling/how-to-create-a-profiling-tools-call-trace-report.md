---
title: Criar um relatório de rastreamento de chamada das Ferramentas de Criação de Perfil | Microsoft Docs
description: Crie um relatório de rastreamento de chamada de ferramentas de desempenho para ver informações de tempo para suas funções e para funções chamadas por suas funções.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 12d294202c3cea2c19f4f88ca4e7bd1dfd62df67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860822"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Como criar um relatório de rastreamento de chamada das ferramentas de criação de perfil
O *relatório de rastreamento de chamada* para as Ferramentas de criação de perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lista informações de tempo para cada ponto de entrada e de saída para as funções do aplicativo e cada chamada para outras funções por sua função. Relatórios de rastreamento de chamada estão disponíveis para criação de perfil de dados somente se foram coletados com o método de instrumentação.

> [!NOTE]
> Você não pode exibir relatórios de rastreamento de chamada no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Você precisa usar a ferramenta de linha de comando **VSPerfReport** para gerar um arquivo de valor separado por vírgula (.*csv*) ou .*xml*. Para obter mais informações sobre essa ferramenta, consulte [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Para criar um relatório de rastreamento de chamada

1. Abra uma janela de **prompt de comando** .

2. No prompt de comando, digite o comando a seguir:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |Item|Descrição|
    |-|-|
    |*ToolsPath*|O caminho para as ferramentas de linha de comando das Ferramentas de Criação de Perfil. Para saber mais, confira [Especificar o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Os dados de criação de perfil (.*VSP* ou. *vsps*) Grupo. Caminhos completos e parciais são aceitos.|
    |Xml|Gera um relatório XML formatado.|

## <a name="see-also"></a>Confira também
- [Como coletar dados do ETW (rastreamento de eventos para Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [APIs de ferramentas de criação de perfil](../profiling/profiling-tools-apis.md)
