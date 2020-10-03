---
title: Diagnóstico de gráficos | Microsoft Docs
description: Uma introdução ao Visual Studio Diagnóstico de Gráficos.
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 829c51c0e2020a154dc485dbfc4db25e0b399e57
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671373"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos do Visual Studio
>[!NOTE]
> O Visual Studio recomenda o PIX no Windows para jogos DirectX 12. O [PIX no Windows](https://aka.ms/PIXonWindows) é uma ferramenta de ajuste e depuração de desempenho que dá suporte total ao DirectX 12. [Saiba mais informações](visual-studio-graphics-diagnostics-directx-12.md) ou [Baixe aqui](https://aka.ms/downloadPIX).

O Visual Studio *diagnóstico de gráficos* é um conjunto de ferramentas para gravar e analisar problemas de desempenho e renderização em aplicativos Direct3D. Diagnóstico de Gráficos pode ser usado em aplicativos que estão sendo executados localmente em seu computador Windows, em um emulador de dispositivo do Windows ou em um computador ou dispositivo remoto.

 O fluxo de trabalho de Diagnóstico de Gráficos começa capturando um registro de como seu aplicativo usa o Direct3D — ao vivo, à medida que é executado — para que seu comportamento possa ser analisado imediatamente, compartilhado ou salvo para mais tarde. As sessões de captura podem ser iniciadas e controladas manualmente no Visual Studio ou com a ferramenta de captura de linha de comando **dxcap.exe**. As sessões de captura também podem ser iniciadas e controladas programaticamente usando as APIs de captura Diagnóstico de Gráficos.

 Depois que uma sessão de captura tiver sido registrada, seu conteúdo poderá ser reproduzido pelo *analisador de gráficos* do Visual Studio a qualquer momento, recriando os quadros capturados usando exatamente os mesmos recursos e processando comandos usados pelo aplicativo. Em seguida, usando as ferramentas fornecidas na janela analisador de gráficos, qualquer um dos quadros capturados pode ser analisado em detalhes. Essas ferramentas podem ser usadas para examinar qualquer chamada à API do Direct3D, recurso, objeto de estado do pipeline, estágio do pipeline ou até mesmo o histórico completo de qualquer pixel em um quadro capturado. Ao usar essas ferramentas em conjunto, um problema de renderização pode ser explorado intuitivamente, começando de como ele aparece em um quadro capturado e fazendo uma busca detalhada em sua causa raiz no código-fonte, nos sombreadores ou nos ativos gráficos do aplicativo.

 Para diagnosticar problemas de desempenho, um quadro capturado pode ser analisado usando a ferramenta de *análise de quadros* . Essa ferramenta explora otimizações de desempenho potenciais alterando automaticamente a maneira como o aplicativo usa Direct3D e benchmarking de todas as variações para você. No passado, você pode ter feito e fazer o benchmark desses tipos de alterações manualmente apenas para descobrir quais fizeram uma diferença. Com a análise de quadros, você só precisa fazer as alterações que já conhecem serão pagas.

 Diagnóstico de Gráficos ajuda sua aparência do aplicativo Direct3D graficamente rica e a melhor execução.

 Continue na [visão geral](overview-of-visual-studio-graphics-diagnostics.md) para saber mais sobre o que o Visual Studio diagnóstico de gráficos oferece.

## <a name="in-this-section"></a>Nesta seção
 [Visão geral](overview-of-visual-studio-graphics-diagnostics.md) Apresenta as ferramentas e o fluxo de trabalho Diagnóstico de Gráficos.

 [Introdução](getting-started-with-visual-studio-graphics-diagnostics.md) Nesta seção, você aprenderá como instalar o Visual Studio Diagnóstico de Gráficos e como começar a usar o Diagnóstico de Gráficos com seu aplicativo do Direct3D.

 [Capturando informações de gráficos](capturing-graphics-information.md) Para usar Diagnóstico de Gráficos para examinar um problema de renderização em seu aplicativo, primeiro você registra informações sobre como o aplicativo usa o DirectX. Durante a sessão de gravação, enquanto o aplicativo é executado normalmente, você *captura* (ou seja, seleciona) os quadros de interesse. A captura contém informações detalhadas sobre como os quadros são renderizados. É possível salvar as informações capturadas como um documento de log de gráficos para examinar mais tarde ou compartilhar com outros membros da equipe.

 [Uso de GPU](../../profiling/gpu-usage.md) Para usar Diagnóstico de Gráficos para criar o perfil de seu aplicativo, use a ferramenta uso de GPU. O uso de GPU pode ser usado em conjunto com outras ferramentas de criação de perfil, como o uso da CPU, para correlacionar a atividade de CPU e GPU que podem contribuir para problemas de desempenho em seu aplicativo.

 [Documento de log de gráficos](graphics-log-document.md) Para iniciar o exame de um log de gráficos gravados, use a janela documento de log de gráficos para selecionar um quadro capturado, ou até mesmo um pixel específico, para que você possa examinar em detalhes os *eventos* (isto é, as chamadas à API do DirectX) que o afetam.

 [Análise de quadros](graphics-frame-analysis.md) Depois de selecionar um quadro, você usa Análise de Quadros de Gráficos para examinar e ajustar o desempenho de renderização.

 [Lista de eventos](graphics-event-list.md) Depois de selecionar um quadro, use a **lista de eventos gráficos** para examinar seus eventos e determinar se eles estão relacionados ao problema de renderização.

 [Estado](graphics-state.md) A janela estado ajuda você a entender o estado de gráficos que está ativo no momento do evento atual.

 [Estágios de pipeline](graphics-pipeline-stages.md) Na janela **estágios de pipeline de gráficos** , você investiga como o evento selecionado atualmente é processado por cada estágio do pipeline de gráficos para que você possa identificar onde o problema de renderização aparece primeiro. Examinar os estágios do pipeline é especialmente útil quando um objeto não aparece devido a uma transformação incorreta ou quando um dos estágios produz uma saída que não corresponde ao que o próximo estágio espera.

 [Pilha de chamadas de evento](graphics-event-call-stack.md) Use a **pilha de chamadas de evento de gráficos** para examinar a pilha de chamadas do evento selecionado no momento para que você possa navegar até o código do aplicativo relacionado ao problema de renderização.

 [Histórico de pixel](graphics-pixel-history.md) Usando a janela **histórico de pixels de gráficos** para analisar como o pixel selecionado atualmente é afetado pelos eventos que o influenciaram, você pode identificar o evento ou a combinação de eventos que causam certos tipos de problemas de processamento. O histórico de pixel é especialmente útil quando um objeto é renderizado incorretamente porque a saída do sombreador de pixel está incorreta ou foi combinada incorretamente com o buffer de quadro, ou quando um objeto não aparece porque seus pixels foram descartados antes de atingir o buffer de quadro.

 [Tabela de objetos](graphics-object-table.md) Use a **tabela de objetos gráficos** para examinar as propriedades e o conteúdo de objetos e recursos específicos do Direct3D que estão em vigor para o evento selecionado no momento. A tabela de objetos pode ajudar a determinar o contexto do dispositivo gráfico que está ativo durante um evento e examinar os conteúdos de recursos gráficos, como buffers constantes, buffers de vértices e texturas.

 [Depurador do HLSL](hlsl-shader-debugger.md) Para examinar como o código de sombreador do estágio do evento e do pipeline de gráficos selecionado se comporta, use o **depurador HLSL** para percorrer o código, examinar o conteúdo das variáveis e executar outras tarefas de depuração típicas. Também é possível usar o depurador HLSL para examinar o código do sombreador de computação, independente de os resultados serem processados mais pelo pipeline de gráficos ou apenas relidos pelo aplicativo.

 [Ferramenta de captura de linha de comando](command-line-capture-tool.md) Use a ferramenta de captura de linha de comando para capturar e reproduzir informações de gráficos rapidamente sem usar o Visual Studio ou a captura programática. Em particular, você pode usar a ferramenta de captura de linha de comando para automação ou em um ambiente de teste.

 [Exemplos](graphics-diagnostics-examples.md) Vários exemplos demonstram como usar as ferramentas de Diagnóstico de Gráficos em conjunto para diagnosticar diferentes tipos de problemas de renderização.

## <a name="related-sections"></a>Seções relacionadas

| Título | Descrição |
| - | - |
| [Tour pelos recursos do depurador](../debugger-feature-tour.md) | Apresenta a funcionalidade de depuração no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Elementos gráficos e jogos do DirectX](/windows/win32/directx) | Fornece artigos que discutem as tecnologias de gráficos do DirectX. |
| [Suporte ao DirectX 12 no Visual Studio](visual-studio-graphics-diagnostics-directx-12.md) | Saiba mais sobre o suporte do DirectX 12 no Visual Studio |
