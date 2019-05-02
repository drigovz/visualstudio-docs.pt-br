---
title: 'Como: Criar um relatório de rastreamento de chamada das Ferramentas de Criação de Perfil | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03c039d0059e3e5768681ece9bb547b0f4eb7783
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432760"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Como: Criar um relatório de rastreamento de chamada das ferramentas criação de perfil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O *relatório de rastreamento de chamada* para as Ferramentas de criação de perfil do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lista informações de tempo para cada ponto de entrada e de saída para as funções do aplicativo e cada chamada para outras funções por sua função. Relatórios de rastreamento de chamada estão disponíveis para criação de perfil de dados somente se foram coletados com o método de instrumentação.  
  
> [!NOTE]
> Você não pode exibir relatórios de rastreamento de chamada no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Você deve usar a ferramenta de linha de comando **VSPerfReport** para gerar um valor separado por vírgula (.csv) ou um arquivo Xml. Para obter mais informações sobre essa ferramenta, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Para criar um relatório de rastreamento de chamada  
  
1. Abra uma janela do **Prompt de Comando**.  
  
2. No prompt de comando, digite o seguinte comando:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|O caminho para ferramentas de linha de comando de ferramentas de criação de perfil. Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Os dados de criação de perfil (arquivo .vsp ou .vsps). Caminhos completos e parciais são aceitos.|  
    |Xml|Gera um relatório Xml formatado.|  
  
## <a name="see-also"></a>Consulte também  
 [Como: Coletar o rastreamento de eventos para Windows (ETW) de dados](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [APIs de ferramentas de criação de perfil](../profiling/profiling-tools-apis.md)
