---
title: Diagnóstico de gráficos | Microsoft Docs
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
ms.openlocfilehash: cbc3edfabe041804a632b919eff4e565be9cc5e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848606"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnóstico de gráficos do Visual Studio
Visual Studio*diagnóstico de gráficos* é um conjunto de ferramentas de registro e, em seguida, analisando problemas de desempenho e a renderização em aplicativos Direct3D. Diagnóstico de gráficos pode ser usado em aplicativos que estão sendo executadas localmente no seu PC com Windows, em um emulador de dispositivo do Windows ou em um dispositivo ou computador remoto.

 O fluxo de trabalho de diagnóstico de gráficos começa com a captura de um registro de como seu aplicativo usa o Direct3D — ao vivo, enquanto ele é executado — para que seu comportamento pode ser analisado imediatamente, compartilhados ou salvas para uso posterior. Sessões de captura podem ser iniciadas e controladas manualmente do Visual Studio ou com a ferramenta de linha de comando de captura **dxcap.exe**. Sessões de captura também podem ser iniciadas e controladas programaticamente usando as APIs de captura do diagnóstico de gráficos.

 Depois que uma sessão de captura foi registrada seu conteúdo pode ser reproduzido pelo Visual Studio *analisador de gráficos* a qualquer momento, recriando os quadros capturados usando os mesmos recursos exatos e o aplicativo usado comandos de renderização. Em seguida, usando as ferramentas fornecidas na janela do analisador de gráficos, qualquer um dos quadros capturados podem ser analisados em detalhes. Essas ferramentas podem ser usadas para examinar qualquer chamada à API do Direct3D, recursos, o objeto de estado do pipeline, estágio de pipeline ou até mesmo o histórico completo de qualquer pixel em um quadro capturado. Usando essas ferramentas em conjunto, um problema de renderização pode ser explorado intuitivamente, começando em como ela aparece em um quadro capturado e aprofundar-se a causa raiz em ativos de código, sombreadores ou elementos gráficos de código-fonte do aplicativo.

 Para diagnosticar problemas de desempenho, um quadro capturado pode ser analisado usando as *análise de quadros* ferramenta. Essa ferramenta explora as otimizações de desempenho potencial automaticamente alterando o modo como o aplicativo usa o Direct3D e benchmark todas as variações para você. No passado, você pode ter feito e por benchmark esses tipos de alterações manualmente apenas para localizar quais fizeram uma diferença de fora. Com análise de quadro, você só precisará fazer as alterações que você já conhece valerá a.

 Diagnóstico de gráficos ajuda seu aplicativo do Direct3D graficamente ricos examinar e executar o melhor desempenho.

 Continuar a [visão geral](overview-of-visual-studio-graphics-diagnostics.md) para saber mais sobre o que oferece diagnóstico de gráficos do Visual Studio.

## <a name="in-this-section"></a>Nesta seção
 [Visão geral](overview-of-visual-studio-graphics-diagnostics.md) apresenta as ferramentas e fluxo de trabalho de diagnóstico de gráficos.

 [Introdução ao](getting-started-with-visual-studio-graphics-diagnostics.md) nesta seção, você aprenderá como instalar o diagnóstico de gráficos do Visual Studio e como começar a usar o diagnóstico de gráficos com seu aplicativo Direct3D.

 [Capturando informações de gráficos](capturing-graphics-information.md) para usar o diagnóstico de gráficos para examinar um problema de renderização em seu aplicativo, primeiro registre informações sobre como o aplicativo usa o DirectX. Durante a sessão de gravação, enquanto o aplicativo é executado normalmente, você *captura* (ou seja, seleciona) os quadros de interesse. A captura contém informações detalhadas sobre como os quadros são renderizados. É possível salvar as informações capturadas como um documento de log de gráficos para examinar mais tarde ou compartilhar com outros membros da equipe.

 [Uso de GPU](gpu-usage.md) para usar o diagnóstico de gráficos para analisar seu aplicativo, use a ferramenta de uso de GPU. Uso de GPU pode ser usado em conjunto com outras ferramentas de criação de perfil, como o uso da CPU, para correlacionar a atividade de CPU e GPU que pode causar problemas de desempenho em seu aplicativo.

 [Documento de Log de gráficos](graphics-log-document.md) para iniciar o exame de um log de gráficos registrado, use a janela do documento de Log de gráficos para selecionar um quadro capturado — ou até mesmo um pixel específico — para que você possa examinar detalhadamente os *eventos* (que é, as chamadas à API DirectX) que afetam a ele.

 [Análise de quadros](graphics-frame-analysis.md) depois de selecionar um quadro, usar análise de quadros de gráficos para examinar e ajustar seu desempenho de renderização.

 [Lista de eventos](graphics-event-list.md) depois de selecionar um quadro, você usar o **lista de eventos gráficos** para examinar os eventos para determinar se eles estão relacionados ao problema de renderização.

 [Estado](graphics-state.md) janela o estado ajuda você a entender o estado dos gráficos que está ativo no momento do evento atual.

 [Estágios de pipeline](graphics-pipeline-stages.md) no **estágios de Pipeline gráficos** janela, você investigar como o evento selecionado no momento é processado pelos estágios de pipeline gráficos para que você possa identificar onde o problema de renderização primeiro é exibida. Examinar os estágios do pipeline é especialmente útil quando um objeto não aparece devido a uma transformação incorreta ou quando um dos estágios produz uma saída que não corresponde ao que o próximo estágio espera.

 [Pilha de chamadas](graphics-event-call-stack.md) você usar o **pilha de chamadas do evento de gráficos** para examinar a pilha de chamadas do evento selecionado no momento para que você pode navegar para o código do aplicativo que está relacionado ao problema de renderização.

 [Histórico de pixel](graphics-pixel-history.md) usando o **histórico de Pixel de gráficos** janela para analisar como o pixel selecionado no momento é afetado pelos eventos que o influenciaram, você pode identificar o evento ou uma combinação de eventos que causam certos tipos de problemas de renderização. O histórico de pixel é especialmente útil quando um objeto é renderizado incorretamente porque a saída do sombreador de pixel está incorreta ou foi combinada incorretamente com o buffer de quadro, ou quando um objeto não aparece porque seus pixels foram descartados antes de atingir o buffer de quadro.

 [Tabela do objeto](graphics-object-table.md) você usar o **tabela de objetos gráficos** para examinar as propriedades e o conteúdo de objetos específicos do Direct3D e recursos que estão em vigor para o evento selecionado no momento. A tabela de objetos pode ajudar a determinar o contexto do dispositivo gráfico que está ativo durante um evento e examinar os conteúdos de recursos gráficos, como buffers constantes, buffers de vértices e texturas.

 [Depurador de HLSL](hlsl-shader-debugger.md) para examinar como o código do sombreador para o estágio de pipeline o evento selecionado no momento e os gráficos se comporta, você deve usar o **depurador HLSL** para percorrer o código, examinar o conteúdo de variáveis e realizar outras tarefas típicas de depuração. Também é possível usar o depurador HLSL para examinar o código do sombreador de computação, independente de os resultados serem processados mais pelo pipeline de gráficos ou apenas relidos pelo aplicativo.

 [Ferramenta de linha de comando de captura](command-line-capture-tool.md) usar a ferramenta de linha de comando de captura para capturar e reproduzir informações gráficas sem usar o Visual Studio ou captura programática rapidamente. Em particular, você pode usar a ferramenta de captura de linha de comando para automação ou em um ambiente de teste.

 [Exemplos](graphics-diagnostics-examples.md) vários exemplos demonstram como usar as ferramentas de diagnóstico de gráficos juntas para diagnosticar diferentes tipos de problemas de renderização.

## <a name="related-sections"></a>Seções relacionadas

| Título | Descrição |
| - | - |
| [Tour dos recursos do depurador](/visualstudio/debugger/debugger-feature-tour) | Apresenta a funcionalidade de depuração no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Gráficos e jogos DirectX](http://go.microsoft.com/fwlink/?LinkId=256498) | Fornece artigos que discutem as tecnologias de gráficos do DirectX. |
