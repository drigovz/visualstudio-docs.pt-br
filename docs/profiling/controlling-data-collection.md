---
title: Controlando a coleta de dados | Microsoft Docs
description: Saiba como iniciar e parar Ferramentas de Criação de Perfil coleta de dados e como limitar os objetos para os quais os dados de criação de perfil são coletados. Este artigo é uma visão geral.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b846db263c95f20c6ea4cb6a418973830a5dd8ee
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720924"
---
# <a name="control-data-collection"></a>Controlar a coleta de dados
As Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permitem controlar quando os dados de criação de perfil são coletados durante uma sessão de desempenho e especificar as funções das quais o perfil será criado. Esta seção descreve como iniciar e parar a coleta de dados nas janelas **Gerenciador de Desempenho** e **Controle de Coleta de Dados** e como limitar os objetos para os quais os dados de criação de perfil são coletados.

## <a name="common-tasks"></a>Tarefas comuns

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Iniciar e parar a criação de perfil:** é possível iniciar a criação de perfil de um aplicativo quando o aplicativo é iniciado ou anexar o criador de perfil a um processo que já está em execução. Quando o aplicativo de destino está em execução, é possível pausar e retomar a coleta de dados. Você encerra uma sessão de criação de perfil fechando o aplicativo de destino ou desanexando o criador de perfil de um processo em execução.|-   [Como iniciar e terminar a coleta de dados de desempenho](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Como anexar e desanexar as ferramentas de desempenho dos processos em execução](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Como pausar e retomar a coleta de dados de desempenho](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Configurar a criação de perfil de instrumentação para limitar os dados coletados:** é possível usar propriedades de configuração de sessão de desempenho para limitar os dados coletados em execuções de criação de perfil que usam o método de instrumentação. É possível incluir ou excluir arquivos .dll, namespaces, classes e funções específicos. Você também pode excluir funções que não atendem a um limite de tamanho especificado.|-   [Como limitar a instrumentação a DLLs específicas](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Como limitar a instrumentação a funções específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Como: excluir ou incluir funções curtas da instrumentação](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>Seções relacionadas
- [Configurar sessões de desempenho](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Confira também
- [Performance Explorer](../profiling/performance-explorer.md)
