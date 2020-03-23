---
title: Coletando dados de tempo detalhados usando a instrumentação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bfd22edc9bd672a8d82c94a705b523ce7d836169
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779617"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Coletar dados de tempo detalhados usando a instrumentação
O método de instrumentação das Ferramentas de Criação [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] injeta código de criação de perfil em uma cópia de um módulo. O código registra cada entrada, saída e a chamada de função das funções no módulo durante uma execução de criação de perfil. O método de instrumentação é útil para coletar informações detalhadas de tempo sobre uma seção do seu código e para compreender o impacto das operações de entrada e saída sobre o desempenho do aplicativo.

 É possível especificar o método de amostragem usando um dos seguintes procedimentos:

- Na primeira página do Assistente de Criação de Perfil, selecione **Instrumentação**.

- Na barra de ferramentas do **Gerenciador de Desempenho**, na lista **Método**, clique em **Instrumentação**.

- Na página **Geral** da caixa de diálogo de propriedades da sessão de desempenho, clique em **Instrumentação**.

## <a name="common-tasks"></a>Tarefas comuns
 Você pode especificar opções adicionais na caixa de diálogo Páginas de**propriedade** de sessão de _desempenho_da sessão de desempenho. Para abrir essa caixa de diálogo:

- No **Performance Explorer,** clique com o botão direito do mouse no nome da sessão de desempenho e clique **em Propriedades**.

  As tarefas na tabela a seguir descrevem opções que você pode especificar na caixa de diálogo **'Páginas de propriedade de** sessão de _desempenho'_ quando você perfilar usando o método de instrumentação.

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|Na página **Geral**, adicione a alocação de memória do .NET e dados de tempo de vida e especifique os detalhes de nomenclatura para o arquivo de dados de criação de perfil gerado (.vsp).|-   [Coletar dados de alocação de memória .NET e de vida](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Como: Definir opções de nome de arquivo de dados de desempenho](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na página **Iniciar**, se você tiver vários projetos .exe em sua solução, especifique o aplicativo a ser iniciado e sua ordem de início.|-   [Como: Especificar o binário para começar](../profiling/how-to-specify-the-binary-to-start.md)|
|Na página **Binários**, especifique um local para as cópias instrumentadas dos módulos. Por padrão, os binários originais são movidos para uma pasta de backup.|-   [Como: Realocar binários instrumentados](../profiling/how-to-relocate-instrumented-binaries.md)|
|Na página **Interação de Camada**, adicione dados de chamada ADO.NET à execução de criação de perfil.|-   [Coletar dados de interação entre camadas](../profiling/collecting-tier-interaction-data.md)|
|Na página **Instrumentação**, exclua pequenas funções de criação de perfil para reduzir a sobrecarga da criação de perfil, criar perfil de código JavaScript em páginas Web ASP.NET e especificar comandos para serem executados em um prompt de comando antes e depois do processo de instrumentação.|-   [Como: Excluir ou incluir funções curtas da instrumentação](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Como: Perfil código JavaScript em páginas da Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Como especificar comandos pré e pós-instrumento](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|Na página **Contadores de CPU**, especifique um ou mais contadores de desempenho de processador para serem adicionados aos dados de criação de perfil.|-   [Como: coletar dados do contador de CPU](../profiling/how-to-collect-cpu-counter-data.md)|
|Na página **Eventos do Windows**, selecione um ou mais eventos ETW (Rastreamento de Eventos para Windows) para coletar com os dados de amostragem.|-   [Como: Coletar rastreamento de eventos para dados do Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na página **Contadores do Windows**, especifique um ou mais contadores de desempenho de sistema operacional para serem adicionados aos dados de criação de perfil como marcas.|-   [Como: Coletar dados do contador do Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na página **Avançado**, especifique outras opções que você deseja passar para o programa de instrumentação VSInstr.exe, como opções para incluir ou excluir funções específicas.|-   [Como: Especificar opções adicionais de instrumentação](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Como: Limitar a instrumentação a funções específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Vsinstr](../profiling/vsinstr.md)|
