---
title: Como você pode aumentar as chances de um problema de desempenho ser corrigido
description: Informações adicionais e melhores práticas para envio de problemas de desempenho no Visual Studio
author: seaniyer
ms.author: seiyer
ms.date: 11/19/2019
ms.topic: reference
ms.openlocfilehash: 119de27298acafee7dc563a30246b18da42f9f29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75918157"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Como aumentar as chances de um problema de desempenho ser corrigido

A ferramenta "[Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019)" é amplamente utilizada pelos usuários do Visual Studio para relatar uma série de problemas. A equipe do Visual Studio detecta tendências de colisão e lentidão no feedback dos usuários e aborda problemas que afetam uma ampla faixa de usuários. Quanto mais acionável for um ticket de feedback específico, maior a probabilidade de ser diagnosticado e resolvido rapidamente pela equipe do produto. Este documento descreve as melhores práticas ao relatar problemas de falha ou lentidão para torná-los mais acionáveis.

## <a name="general-best-practices"></a>Práticas recomendadas gerais

Visual Studio é uma plataforma grande e complexa que suporta uma infinidade de idiomas, tipos de projetos, plataformas e muito mais. Como ele funciona é uma função de quais componentes são instalados e ativos em uma sessão, as extensões instaladas, as configurações do Visual Studio, a configuração da máquina e, finalmente, a forma do código que está sendo editado. Dado o número de variáveis, é difícil dizer se o relatório de problemas de um usuário tem o mesmo problema que um relatório de problema de outro usuário, mesmo que o sintoma visível seja o mesmo. Dado isso, aqui estão algumas práticas recomendadas para garantir que seu relatório de problemas específicos tenha maior probabilidade de ser diagnosticado.

**Forneça um título tão específico quanto possível**

Procure assinaturas distintas para o problema que está sendo relatado e inclua o máximo possível no título. Se o título for descritivo, é menos provável que usuários com problemas não relacionados (mas mesmo sintoma superficial) votem ou comentem sobre seu ticket, dificultando assim o diagnóstico do *seu* problema.

**Na dúvida, registre um novo relatório de problemas**

Muitos problemas podem não ter nenhuma assinatura ou passos distintos para reproduzir. Nesses casos, um novo relatório é melhor do que um upvote ou um comentário sobre outro relatório, que está relatando um *sintoma*externo semelhante . Dependendo do tipo de relatório, inclua arquivos de diagnóstico adicionais ao seu relatório, conforme descrito posteriormente neste documento.

**Práticas recomendadas específicas para problemas**

Descritos abaixo são problemas difíceis de diagnosticar sem bons arquivos de diagnóstico. Depois de identificar o caso que melhor descreve seu problema, siga as etapas de feedback específicas para esse caso.

-   [Travas:](#crashes) Um acidente ocorre quando o processo (Visual Studio) termina inesperadamente.

-   [Não responder:](#unresponsiveness) O VS fica sem resposta por um longo período de tempo.

-   [Problemas de lentidão:](#slowness-and-high-cpu-issues) Qualquer ação específica em VS é mais lenta do que o desejado

-   [CPU alta:](#slowness-and-high-cpu-issues) Períodos prolongados de uso de CPU inesperadamente alto

-   [Problemas fora do processo:](#out-of-process-issues) Um problema causado por um processo de satélite do Visual Studio

## <a name="crashes"></a>Falhas
Um acidente ocorre quando o processo (Visual Studio) termina inesperadamente.

**Acidentes diretamente reprodutíveis**

Acidentes diretamente reprodutíveis são casos que têm todas as seguintes características:

- Pode ser observado seguindo um conjunto conhecido de passos

- Pode ser observado em vários computadores (se disponível)

- Pode ser reproduzido em código de amostra ou um projeto que pode ser vinculado ou fornecido como parte do feedback (se as etapas envolvem a abertura de um projeto ou documento)

Para esses problemas, siga as etapas em "[Como relatar um problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)" e certifique-se de incluir:

-   Os passos para reproduzir o problema

-   Um projeto de repro autônomo como descrito acima. Se a repro autônoma não for possível, por favor inclua:

    -   A linguagem dos projetos\#abertos (C, C++, etc.)

    -   O tipo de projeto (Console Application, ASP.NET, etc.)


> [!NOTE]
> **Feedback mais valioso:** Para este caso, o feedback mais valioso é o conjunto de etapas para reproduzir o problema juntamente com o código fonte da amostra.

**Acidentes desconhecidos**

Se você não tem certeza do que está causando seus acidentes ou eles parecem aleatórios, então você pode capturar dumps localmente cada vez que o Visual Studio falhar e anexá-los a itens de feedback separados. Para salvar dumps localmente quando o Visual Studio falhar, execute os seguintes comandos em uma janela de comando do administrador:

```
reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe"

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpType /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpCount /t REG_DWORD /d 2

reg add "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\Windows Error
Reporting\\LocalDumps\\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\\CrashDumps"
```

Personalize a contagem de despejos e a pasta de despejo conforme apropriado. Encontre mais informações sobre essas configurações [aqui](/windows/win32/wer/collecting-user-mode-dumps).

> [!NOTE]
> Os dumps capturados usando o Gerenciador de Tarefas provavelmente serão da morderiedade errada, o que os torna menos utilizáveis. O procedimento descrito acima é a maneira preferida de capturar um lixão. Se você quiser usar o Task Manager, feche o que está em execução no\\momento, inicie o\\Gerenciador de Tarefas de 32bits (%windir% syswow64 taskmgr.exe) e colete um dump de pilha de lá.

> [!NOTE] 
> Cada arquivo de despejo produzido por este método terá até 4 GB de tamanho. Certifique-se de definir DumpFolder para um local com espaço de unidade adequado ou ajustar o DumpCount adequadamente.

Cada vez que o Visual Studio falhar, ele criará um arquivo de despejo **devenv.exe.[ número].dmp** arquivo no local configurado.

Em seguida, use "Report a Problem..." do Visual Studio Recurso. Ele permitirá que você anexe o lixão apropriado.

1.  Localize o arquivo de despejo para o acidente que você está relatando (procure um arquivo com o tempo de criação correto)

2.  Se possível, feche\*o arquivo (.zip) para reduzir seu tamanho antes de enviar feedback

3.  Siga as etapas em "[Como relatar um problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)", e anexe o dump de pilha a um novo item de feedback.

> [!NOTE] 
> **Feedback mais valioso:** Para este caso, o feedback mais valioso é o depósito de pilhas capturado no momento do acidente.

## <a name="unresponsiveness"></a>Apatia
O VS fica sem resposta por um longo período de tempo.

**Inrespondível diretamente**

Como descrito na seção correspondente sobre acidentes, para problemas que podem ser facilmente reproduzidos, vistos em várias máquinas e podem ser demonstrados em uma pequena amostra, os relatórios de feedback mais valiosos são aqueles que incluem etapas para reproduzir o problema, e incluem código fonte de amostra que demonstra o problema.

**Não responde desconhecido**

Se uma falta de resposta se manifestar de forma imprevisível, na próxima ocorrência, lance uma nova instância do Visual Studio e reporte um problema a partir dessa instância.
Na [tela "Gravar",](/visualstudio/ide/how-to-report-a-problem-with-visual-studio?view=vs-2019#record-a-repro)certifique-se de selecionar a sessão do Visual Studio que não responde.

Se a instância do Visual Studio que não responde foi lançada no modo Administrador, então a segunda instância também precisaria ser lançada no modo Administrador.

>[!NOTE] 
> **Feedback mais valioso:** Para este caso, o feedback mais valioso é o despejo de pilha capturado no momento da Falta de Resposta.

## <a name="slowness-and-high-cpu-issues"></a>Lentidão e problemas elevados de CPU

O que torna um problema de lentidão ou alto uso de CPU mais acionável é um traço de desempenho capturado enquanto a operação lenta ou o evento de alta CPU está em andamento.

>[!NOTE] 
> Quando possível, isole cada cenário em um relatório de feedback separado e específico.
Por exemplo, se a digitação e a navegação forem lentas, siga as etapas abaixo uma vez por edição. Isso ajuda a equipe do produto a isolar a causa de problemas específicos.

Para obter melhores resultados na captura do desempenho, siga estas etapas:

1.  Se ainda não estiver em execução, tenha uma cópia do Visual Studio aberta onde você irá reproduzir o problema

    -   Tenha tudo configurado para reproduzir o problema. Por exemplo, se você precisar de um projeto específico para ser carregado com um arquivo específico aberto, então certifique-se de que ambas as etapas estão concluídas antes de prosseguir.

    -   Se você *não* estiver relatando um problema específico para carregar uma solução, tente esperar de 5 a 10 minutos (ou mais, dependendo do tamanho da solução) depois de abrir a solução antes de gravar o rastreamento de desempenho. O processo de carga de solução produz uma grande quantidade de dados, então esperar por alguns minutos nos ajuda a focar no problema específico que você está relatando.

2.  Inicie uma segunda cópia do Visual Studio *sem solução aberta*

3.  Na nova cópia do Visual Studio, abra a ferramenta **Report a Problem**

4.  Siga as etapas em [Como Relatar um Problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) até chegar à etapa "Fornecer um rastreamento e um dump de pilha (opcional)".

5.  Escolha gravar a primeira cópia do Visual Studio (aquela que encontra problema de desempenho) e comece a gravar.

    -   O aplicativo Steps Recorder aparecerá e começará a gravar.

    -   **Durante a gravação,** realize a ação problemática na primeira cópia do Visual Studio. É difícil para nós corrigir problemas específicos de desempenho se eles não aparecerem dentro do tempo registrado.

    -   Se a ação for menor que 30 segundos e puder ser facilmente repetida, repita a ação para demonstrar ainda mais o problema.

    -   Para a maioria dos casos, um traço de 60 segundos é suficiente para demonstrar os problemas, especialmente se a ação problemática durou (ou foi repetida) por mais de 30 segundos. A duração pode ser ajustada conforme necessário para capturar o comportamento que você gostaria de fixar.

6.  Clique em "Stop Record" no Steps Recorder assim que a operação lenta ou o evento de alta CPU que você deseja relatar estiver concluído. Pode levar alguns minutos para processar o rastreamento de desempenho.

7.  Uma vez concluído, haverá vários anexos ao seu feedback. Anexar quaisquer arquivos adicionais que possam ajudar a reproduzir o problema (um projeto de amostra, capturas de tela, vídeos, etc.).

8.  Envie o feedback.

Ao gravar um rastreamento de desempenho, se a operação lenta ou alta CPU que você está relatando chegar ao fim, então interrompa imediatamente a gravação. Se muitas informações forem coletadas, as informações mais antigas são sobreescritas. Se o rastreamento não for interrompido em breve (dentro de alguns segundos) após a operação interessante, os dados de rastreamento úteis serão substituídos.

Não anexe diretamente os traços de desempenho aos itens de feedback existentes no site da Comunidade de Desenvolvedores. Solicitar/fornecer informações adicionais é um fluxo de trabalho suportado na ferramenta Relatório um Problema incorporado do Visual Studio. Se um rastreamento de desempenho for necessário para resolver um item de feedback anterior, definiremos o estado do item de feedback como "Need More Info", que pode ser respondido da mesma forma que relatar um novo problema. Para obter instruções detalhadas, consulte a [seção "Precisar de mais informações"](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017?view=vs-2017#when-further-information-is-needed-need-more-info) no documento 'Relatar um problema'.

> [!NOTE] 
> **Feedback mais valioso:** Para quase todos os problemas de lentidão/alta CPU, o feedback mais valioso é uma descrição\*de alto nível do que você estava tentando fazer, juntamente com o rastreamento de desempenho (.etl.zip) que captura o comportamento durante esse tempo.

**Traços avançados de desempenho**

Os recursos de coleta de rastreamento na ferramenta Relatório-um-problema são suficientes para a maioria dos cenários. Mas há momentos em que é necessário mais controle sobre a coleta de vestígios (por exemplo, rastreamento com um tamanho de buffer maior), nesse caso o PerfView é uma ótima ferramenta para usar. Etapas para gravar manualmente o rastreamento de desempenho usando a ferramenta PerfView podem ser encontradas nos traços de desempenho de gravação com a página [PerfView.](https://github.com/dotnet/roslyn/wiki/Recording-performance-traces-with-PerfView)

## <a name="out-of-process-issues"></a>Problemas fora do processo

> [!NOTE]
> A partir da versão 16.3 do Visual Studio 2019, os logs fora de processo são automaticamente anexados aos comentários enviados usando a ferramenta Report a Problem. No entanto, se o problema for diretamente reproduzível, seguir as etapas abaixo ainda pode ajudar a adicionar informações adicionais para ajudar a diagnosticar melhor o problema.

Há uma série de processos de satélite que correm paralelamente ao Visual Studio e fornecem vários recursos de fora do processo principal do Visual Studio. Se ocorrer um erro em um desses processos de satélite, ele geralmente é visto no lado do Visual Studio como um 'StreamJsonRpc.RemoteInvocationException' ou 'StreamJsonRpc.ConnectionLostException'.

O que torna esses tipos de problemas mais acionáveis é fornecer registros adicionais que podem ser coletados seguindo estas etapas:

1.  Se este for um problema diretamente reproduzível, comece excluindo a pasta **%temp%/servicehub/logs.** Se você não puder reproduzir este problema, mantenha esta pasta intacta e ignore as seguintes balas:

    -   Defina a variável de ambiente global **ServiceHubTraceLevel** como **tudo**
    -   Reproduza o problema.

2.  Baixe a ferramenta microsoft visual studio e .NET framework log collection [tool aqui](https://www.microsoft.com/download/details.aspx?id=12493). .
3.  Execute a ferramenta. Isso produz um arquivo zip para **%temp%/vslogs.zip**. Por favor, anexe esse arquivo ao seu comentário.

## <a name="see-also"></a>Confira também

* [Opções de comentários do Visual Studio](../ide/feedback-options.md)
* [Relatar um problema com o Visual Studio para Mac](/visualstudio/mac/report-a-problem)
* [Relatar um problema com C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Comunidade de desenvolvedores do Estúdio Visual](https://developercommunity.visualstudio.com/)
* [Privacidade de dados da Comunidade de Desenvolvedores](developer-community-privacy.md)
