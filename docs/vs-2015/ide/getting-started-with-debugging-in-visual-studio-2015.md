---
title: Introdução com a depuração no Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 08e317555042bbc63707cc6eccd0177e78b6ddcc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645662"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Introdução à depuração no Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Visual Studio 2015 fornece um poderoso conjunto integrado de ferramentas de compilação e depuração do projeto. Neste tópico, descubra como começar a usar o conjunto mais básico de recursos de interface do usuário de depuração.

 Observação: links para recursos mais avançados e tópicos específicos de plataforma ou de recurso estão na parte inferior desta página.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Meu código não funciona. Ajude-me, Visual Studio 2015!
 Então você descobriu o editor e criei alguns códigos. Agora, você deseja iniciar a depuração desse código. No Visual Studio 2015, assim como acontece com a maioria dos IDEs, há duas fases para depuração: compilar o código para detectar e resolver erros de compilador e de projeto e executar esse código no ambiente para detectar e resolver erros de tempo de execução e dinâmicos.

### <a name="configuring-a-build"></a>Configurando um build
 Há dois tipos básicos de configuração de build: **Depuração** e **Versão**. A primeira configuração produz um executável maior e mais lento que permite uma experiência de depuração de tempo de execução interativa mais avançada, mas nunca deve ser enviado. A segunda compila um executável mais rápido e mais otimizado apropriado para enviar (pelo menos da perspectiva do compilador).

 A configuração de build padrão é **Depuração**.

 ![Botão de compilação de depuração do Visual Studio](../ide/media/vs-ide-gs-debug-build-type1.PNG "|::ref1::|")

 Você também pode especificar uma plataforma de build específica para o destino, como **x86** (CPUs Intel de 32 bits), **x64** (CPUs Intel de 64 bits) e **ARM** (CPUs ARM, com suporte apenas para determinados tipos de aplicativo). O padrão é **x86** para projetos gerenciados e nativos. Para alterá-lo, clique no menu suspenso de plataforma de build e selecione uma plataforma diferente ou **Gerenciador de Configurações...**

 ![Janela do Gerenciador de arquivos de configuração do Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "|::ref2::|")

 Você pode especificar uma configuração de build de destino usando o **Gerenciador de Configurações**. Inicie-o, clique na lista suspensa **Configuração** ou **CPU** e selecione **Novo...** para criar uma nova plataforma ou build.

 ![Janela de Configuration Manager do Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "|::ref3::|")

 Ao começar, basta usar **Depuração** e **x86** como sua configuração de build e plataforma, respectivamente. Quando você terminar de codificar e depurar, altere a configuração para **Versão** e direcione para uma plataforma específica. (As versões mais antigas do Visual Studio forneciam uma plataforma padrão **AnyCPU** para projetos de código .Net.)

 Observação: quando você compila seu projeto, os valores de configuração e plataforma também são usados para determinar que caminho de diretório do projeto é criado para armazenar o executável. Normalmente, ele é **\<caminho-para-o-projeto>\\<nome-do-projeto>\>\\<configuração\>\\<plataforma\>** . Por exemplo, um projeto com uma configuração de `Debug` e uma plataforma de `x86` seria encontrado em `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. Isso poderá ser útil se você tiver suas próprias ferramentas ou scripts que gerenciam esses executáveis compilados.

### <a name="building-your-code"></a>Compilando seu código
 Com seu build configurado, é hora de realmente compilar seu projeto. A maneira mais fácil de fazer isso é pressionar F7, mas você também pode iniciar o build selecionando **Compilar->Compilar Solução** no menu principal.

 ![Seleção do menu de projeto de build do Visual Studio](../ide/media/vs-ide-gs-debug-build-menu-item.png "|::ref4::|")

 Você pode observar o processo de build na janela de status **Saída** na parte inferior da interface do usuário do Visual Studio. Os erros, avisos e operações de build são exibidos aqui. Se você tiver erros (ou se tiver um aviso acima de um nível configurado), haverá falha no build. Você pode clicar nos erros e avisos para ir para a linha em que eles ocorreram. Recompile o projeto pressionando **F7** novamente (para recompilar apenas os arquivos com erros) ou **Ctrl+Alt+F7** (para uma recompilação completa e limpa).

 Há duas janelas com abas de build na janela de resultados abaixo do editor: a janela **Saída**, que contém a saída bruta do compilador (incluindo mensagens de erro) e a janela **Lista de Erros**, que fornece uma lista filtrável e classificável de todos os erros e avisos.

 Quando bem-sucedida, você verá resultados semelhantes a esse na janela **Saída**.

 ![Saída de build bem-sucedida do Visual Studio](../ide/media/vs-ide-gs-debug-success-build.PNG "|::ref5::|")

### <a name="reviewing-the-error-list"></a>Revisando a Lista de Erros
 A menos que não tenha feito nenhuma modificação no código compilado com êxito anteriormente, provavelmente você tem um erro. Se você não estiver familiarizado com a codificação, provavelmente terá muitos deles. Às vezes os erros são óbvios, como um erro de sintaxe simples ou um nome de variável incorreto e às vezes eles são difíceis de entender, com apenas um código confuso para orientá-lo. Para uma exibição mais clara dos problemas, navegue até o final da janela **Saída** do build e clique na guia **Lista de Erros**. Isso leva a uma exibição mais organizada dos erros e avisos para o projeto e oferece algumas opções adicionais também.

 ![Lista de Erros e saída do Visual Studio 2015](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "|::ref6::|")

 Clique na linha de erro na janela **Lista de Erros** e pule para a linha em que ocorre o erro. (Ou ative os números de linha clicando na barra **Início Rápido** na parte superior direita, digitando "números de linha" nela e pressionando Enter. Essa é a maneira mais rápida para chegar à entrada da janela **Opções** em que é possível ativar os números de linha. Saiba como usar a barra **Início Rápido** e poupe muitos cliques na interface do usuário!)

 ![Editor do Visual Studio com números de linha](../ide/media/vs-ide-gs-debug-line-numbers.png "|::ref7::|")

 ![Opção de números de linha do Visual Studio](../ide/media/vs-ide-gs-debug-options-line-numbers.png "|::ref8::|")

 Use Ctrl+G para ir rapidamente para o número de linha em que ocorreu o erro.

 O erro é identificado por um sublinhado vermelho de "rabisco". Passe o mouse sobre ele para obter detalhes adicionais. Faça a correção e ele desaparecerá, embora você possa inserir um novo erro com a correção. (Isso é chamado de "regressão".)

 ![Focalização de erro do Visual Studio](../ide/media/vs-ide-gs-debug-error-hover1.png "|::ref9::|")

 Percorra a lista de erros e resolva todos os erros em seu código.

 ![Janela Depurar erros do Visual Studio](../ide/media/vs-ide-gs-debug-error-list.PNG "|::ref10::|")

### <a name="reviewing-errors-in-detail"></a>Revisando os erros detalhadamente
 Muitos erros podem não fazem sentido para você, formulados como eles estão nos termos do compilador. Nesses casos, você precisará de informações adicionais. Na janela **Lista de Erros**, você pode realizar uma pesquisa automática do Bing para obter mais informações sobre o erro (ou aviso) clicando com o botão direito do mouse na linha de entrada correspondente e selecionando **Mostrar Ajuda para Erros** no menu de contexto.

 ![Lista de erros do Visual Studio da pesquisa do Bing](../ide/media/vs-ide-gs-debug-error-list-error-help.png "|::ref11::|")

 Isso inicia uma guia dentro do Visual Studio 2015 que hospeda os resultados de uma pesquisa do Bing para o código de erro e o texto. Os resultados são de muitas origens diferentes na Internet e nem todos podem ser úteis.

 Como alternativa, você pode clicar no valor do código de erro com hiperlinks na coluna **Código** da **Lista de Erros**. Isso inicializará uma pesquisa do Bing apenas do código de erro.

### <a name="performing-static-code-analysis"></a>Realizando a análise de código estático
 "Análise de código estático" é uma forma elegante de dizer "verificar automaticamente meu código quanto a problemas comuns que podem levar a erros em tempo de execução ou problemas no gerenciamento do código". Crie o hábito de executá-lo depois de limpar os erros óbvios que impediam o build e reserve um tempo para resolver os avisos que ele pode produzir. Você poupará algumas dores de cabeça no futuro, bem como aprenderá algumas técnicas de estilo de código.

 Pressione Alt+F11 (ou selecione **Analisar->Executar Análise de Código na Solução** no menu superior) para iniciar a análise de código estático. Isso poderá levar algum tempo se você tiver muito código.

 ![Item de menu de análise de código do Visual Studio 2015](../ide/media/vs-ide-gs-debug-run-code-analysis.png "|::ref12::|")

 Os avisos novos ou atualizados aparecerão na guia **Lista de Erros** na parte inferior do IDE. Clique nos avisos para acessá-los.

 ![Lista de Erros do Visual Studio 2015 com avisos](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "|::ref13::|")

 Os avisos serão identificados com um rabisco verde-amarelo brilhante em vez de um vermelho. Passe o mouse sobre eles para obter mais detalhes e clique com o botão direito do mouse neles para obter um menu de contexto para auxiliar nas opções de correção ou refatoração.

 ![Foco de aviso de análise de Visual Studio Code](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "|::ref14::|")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Usando as lâmpadas para corrigir ou refatorar o código
 As lâmpadas são um novo recurso para o Visual Studio 2015 que permite refatorar o código embutido. Elas são uma maneira fácil de corrigir avisos comuns com rapidez e eficiência. Para acessá-las, clique com botão direito do mouse em um rabisco de aviso (ou pressione Ctrl+. ao passar o mouse sobre o rabisco) e, em seguida, selecione **Ações Rápidas**.

 ![Opções rápidas de lâmpada do Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb1.png "|::ref15::|")

 Você verá uma lista de possíveis correções ou refatorações que podem ser aplicadas àquela linha de código.

 ![Visualização de lâmpada do Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "|::ref16::|")

 As lâmpadas podem ser usadas sempre que os analisadores de código determinem que há uma oportunidade para corrigir, refatorar ou melhorar seu código. Clique em qualquer linha de código, clique com botão direito do mouse para abrir o menu de contexto e selecione **Ações Rápidas** (ou, novamente, se preferir eficiência, pressione Ctrl+.). Se houver opções de melhoria ou refatoração de área disponíveis, elas serão exibidas, caso contrário, a mensagem `No quick options available here` será exibida no bisel do canto inferior esquerdo do IDE.

 ![Texto ' no Option ' de lâmpada do Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "|::ref17::|")

 Com a experiência, você poderá usar rapidamente as teclas de direção e Ctrl+. para verificar se há oportunidades de refatoração da Opção Rápida e limpar seu código.

 Para obter mais informações sobre as lâmpadas, leia [Realizar ações rápidas com lâmpadas](../ide/perform-quick-actions-with-light-bulbs.md).

### <a name="debugging-your-running-code"></a>Depurando seu código em execução
 Agora que você compilou seu código com êxito e realizou um pouco de limpeza, execute-o pressionando F5 ou selecionando **Depurar->Iniciar Depuração**. Isso iniciará o aplicativo em um ambiente de depuração para que você pode observar seu comportamento em detalhes. O IDE do Visual Studio 2015 muda enquanto o aplicativo é executado: a janela de **Saída** é substituída por duas novas (na configuração de janela padrão), a janela com guias **Autos/Locais/Módulos/Inspeção** e a janela com guias **Pilha de Chamadas/Pontos de Interrupção/Configurações de Exceção/Saída**. Essas janelas têm várias guias que permitem inspecionar e avaliar as variáveis, os threads, as filas de chamadas e vários outros comportamentos do aplicativo enquanto ele é executado.

 ![VS2015 automáticos e janelas de pilha de chamadas](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "|::ref18::|")

 Tente várias ações com seu aplicativo e observe as alterações. Se algo parecer anormal, pause o aplicativo pressionando Ctrl+Alt+Break (ou clique no botão **Pausar**).

 ![Botão interromper tudo do Visual Studio](../ide/media/vs-ide-gs-debug-break-all-button.png "|::ref19::|")

 Pressione F5 para continuar a execução do aplicativo (ou clique no botão **Continuar**).

 ![Botão de depuração de continuação do Visual Studio](../ide/media/vs-ide-gs-debug-continue-button.png "|::ref20::|")

 Você pode parar o aplicativo pressionando Shift+F5 ou clicando no botão **Parar**. Ou, pode simplesmente fechar a janela principal do aplicativo (ou caixa de diálogo de linha de comando).

 Se seu código for executado perfeitamente e exatamente como esperado, parabéns! Altere a configuração de build para **Versão** e recompile-o para implantação. (No entanto, os profissionais talvez desejem pular para a parte sobre Teste de unidade no final.) No entanto, se ele parou, falhou ou forneceu alguns resultados estranhos, você precisará localizar a origem desses problemas e corrigir os bugs.

### <a name="setting-simple-breakpoints"></a>Configuração pontos de interrupção simples
 Pontos de interrupção são o recurso mais básico e essencial da depuração confiável. Um ponto de interrupção indica quando o Visual Studio deve suspender o código em execução para que você possa examinar os valores das variáveis ou o comportamento de memória ou se uma ramificação de código está sendo executada ou não. Você NÃO precisa recompilar um projeto após configurar e remover pontos de interrupção.

 Defina um ponto de interrupção clicando na margem distante da linha em que você deseja que a interrupção ocorra ou selecione a linha de código e pressione F9. Quando você executar o código, ele será parado antes que as instruções para esta linha de código sejam executadas.

 ![Ponto de interrupção do Visual Studio](../ide/media/vs-ide-gs-debug-breakpoint1.png "|::ref21::|")

 Quando o código for parado, a linha de código marcada ainda não terá sido executada. Neste ponto, convém executar as instruções para a linha de código marcada pelo ponto de interrupção e inspecionar os valores alterados. Isso é chamado de “intervir” no código. Se o código marcado for uma chamada de método, você poderá intervir nele pressionando F11. Você também pode "ultrapassar" a linha de código pressionando F10. Para obter mais detalhes sobre as ações da etapa de ponto de interrupção, leia [Navegar pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md).

 Os usos comuns para os pontos de interrupção incluem:

1. Para restringir a origem de uma falha ou travamento, dispersá-la ao longo e ao redor do código da chamada de método que você acredita que está causando a falha. Conforme você percorre o código, remova e redefina os pontos de interrupção mais próximos até encontrar a linha de código incorreta.

2. Ao introduzir um novo código, defina um ponto de interrupção no início dele e percorra o código para verificar se ele está se comportando conforme o esperado.

3. Se tiver implementado um comportamento complicado, defina pontos de interrupção para o código de algoritmo para que você possa inspecionar os valores das variáveis e dados quando o programa for interrompido.

4. Se estiver escrevendo código C ou C++, use de pontos de interrupção para parar o código para que você possa inspecionar os valores de endereço (procure por NULL) e contagens de referência ao depurar para falhas relacionadas à memória.

   Para obter mais informações sobre como usar pontos de interrupção, leia [Usando pontos de interrupção](../debugger/using-breakpoints.md)

### <a name="setting-conditional-breakpoints"></a>Configurando pontos de interrupção condicionais
 Se você tiver um ponto de interrupção em um loop ou recursão ou se tiver muitos pontos de interrupção que percorre com frequência, use um ponto de interrupção condicional para garantir que seu código seja suspenso APENAS quando condições específicas forem atendidas. Caso contrário, você pressionará F11 muitas vezes.

 Para definir um ponto de interrupção condicional e suspender seu código quando uma variável for definida para um determinado valor ou passar um certo limite, clique na margem para definir um ponto de interrupção e, em seguida, selecione a "engrenagem" no menu de foco que aparece.

 ![Configurações de ponto de interrupção do Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "|::ref22::|")

 Você verá uma caixa de diálogo semelhante a essa em que pode definir condições específicas para que a interrupção ocorra.

 ![Ponto de interrupção condicional do Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "|::ref23::|")

 Para obter mais detalhes de como declarar as expressões usadas para avaliar os pontos de interrupção condicionais, confira o vídeo do Channel9 [Breakpoint Configuration Experience in Visual Studio 2015](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711) (Experiência de configuração de ponto de interrupção no Visual Studio).

### <a name="inspecting-your-code-at-run-time"></a>Inspecionando seu código em tempo de execução
 Quando o código em execução atinge um ponto de interrupção e é interrompido, você pode inspecionar variáveis e pilhas de chamadas para determinar o que está acontecendo. Os valores estão nos intervalos que você espera ver? As chamadas estão sendo feitas na ordem correta?

 ![Inspeção do valor de&#45;tempo de execução do Visual Studio 2015](../ide/media/vs-ide-gs-debug-inspect-value.PNG "|::ref24::|")

 Passe o mouse sobre uma variável para ver os valores e referências que ela contém no momento. Se você vir um valor que não esperava, provavelmente haverá um bug nas linhas de código anteriores ou de chamada. Mova os pontos de interrupção para cima ou adicione condições aos pontos de interrupção existentes para restringir ainda mais sua pesquisa.

 Além disso, o Visual Studio 2015 exibe a janela Ferramentas de Diagnóstico, em que você pode observar a utilização de CPU e memória do seu aplicativo ao longo do tempo. Use-os para procurar alocação de memória ou uso da CPU intenso inesperado. Use-o em conjunto com a janela **Inspeção** e pontos de interrupção para determinar o que está causando os recursos não liberados ou o uso intenso inesperado.

 ![Janela de Ferramentas de Diagnóstico do Visual Studio 2015](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "|::ref25::|")

### <a name="running-unit-tests"></a>Executando testes de unidade
 Testes de unidade são programas que executam caminhos de código no aplicativo ou serviço. O Visual Studio 2015 instala as estruturas de teste de unidade da Microsoft para código gerenciado e nativo. Use uma estrutura de teste de unidade para criar testes de unidade, executá-los e relatar os resultados desses testes. Execute os testes de unidade novamente quando realizar alterações para testar se o código ainda está funcionando corretamente. Ao usar o Visual Studio 2015 Enterprise, você pode executar testes automaticamente após cada compilação.

 Para começar, leia [Gerar testes de unidade para seu código com IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

 Para saber mais sobre os testes de unidade no Visual Studio 2015 e como eles podem ajudá-lo a criar um código de qualidade melhor, leia [noções básicas de teste de unidade](../test/unit-test-basics.md).

## <a name="see-also"></a>Veja também
 [Depuração nas configurações do depurador do Visual Studio e depuração de](../debugger/debugging-in-visual-studio.md) [preparação](../debugger/debugger-settings-and-preparation.md) [aplicativos de 64 bits](../debugger/debug-64-bit-applications.md) [noções básicas do depurador](../debugger/debugger-basics.md)
