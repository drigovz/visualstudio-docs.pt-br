---
title: Controlando a coleta de dados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89c1f0b435790622bee54b6cf91d57bd0cc9be29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848779"
---
# <a name="control-data-collection"></a>Controlar a coleta de dados
As Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permitem controlar quando os dados de criação de perfil são coletados durante uma sessão de desempenho e especificar as funções das quais o perfil será criado. Esta seção descreve como iniciar e parar a coleta de dados nas janelas **Gerenciador de Desempenho** e **Controle de Coleta de Dados** e como limitar os objetos para os quais os dados de criação de perfil são coletados.  
  
## <a name="common-tasks"></a>Tarefas comuns
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Iniciar e parar a criação de perfil:** É possível iniciar a criação de perfil de um aplicativo quando o aplicativo é iniciado ou anexar o criador de perfil a um processo que já está em execução. Quando o aplicativo de destino está em execução, é possível pausar e retomar a coleta de dados. Você encerra uma sessão de criação de perfil fechando o aplicativo de destino ou desanexando o criador de perfil de um processo em execução.|-   [Como: Iniciar e encerrar a coleta de dados de desempenho](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Como: Anexar ferramentas de desempenho aos processos em execução e desanexá-las](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Como: Pausar e retomar a coleta de dados de desempenho](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Configure a criação de perfil de instrumentação para limitar os dados coletados:** É possível usar propriedades de configuração de sessão de desempenho para limitar os dados coletados em execuções de criação de perfil que usam o método de instrumentação. É possível incluir ou excluir arquivos .dll, namespaces, classes e funções específicos. Você também pode excluir funções que não atendem a um limite de tamanho especificado.|-   [Como: Limitar a instrumentação a DLLs específicas](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Como: Limitar a instrumentação a funções específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Como: Excluir ou incluir funções curtas de instrumentação](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Configurar sessões de desempenho](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciador de Desempenho](../profiling/performance-explorer.md)