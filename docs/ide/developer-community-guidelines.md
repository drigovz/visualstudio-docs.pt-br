---
title: Diretrizes do Developer Community
description: Descreve as diretrizes para trabalhar com a comunidade de desenvolvedores do Visual Studio.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e30dcb6a9d65cb562851ed90e350530759975d2
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668554"
---
# <a name="developer-community-guidelines"></a>Diretrizes do Developer Community

A comunidade de desenvolvedores rastreia problemas e sugestões de recursos para o Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Enviando problemas e sugestões

A [comunidade de desenvolvedores do Visual Studio](https://aka.ms/feedback/suggest?space=8) rastreia problemas e sugestões de recursos para o Visual Studio.

### <a name="before-submitting-an-issue"></a>Antes de enviar um problema

Procure seu problema na Comunidade de desenvolvedores do Visual Studio para garantir que ela ainda não exista. Se você achar que o problema já existe, faça comentários relevantes e converta seu voto.

Se seu problema for uma pergunta, peça à Comunidade [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) usando a marca _Visual-Studio_. Temos a equipe de suporte ao cliente que está monitorando essa marca e ajudará a responder as perguntas.

Se você não encontrar um problema existente que descreva seu bug ou recurso, envie um problema usando as diretrizes abaixo.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Escrevendo um bom relatório de bugs ou sugestão de recursos

- Arquivo apenas um problema ou solicitação de recurso por problema.

  - A combinação de vários problemas ou de solicitações de recursos em um único problema dificulta nosso diagnóstico e dificulta a votação do seu problema.
  - Não adicione seu problema como um comentário a um problema existente, a menos que seja para uma entrada idêntica. Muitos problemas parecem semelhantes, mas têm causas diferentes, o que torna mais difícil diagnosticar seu problema.

- Quanto mais informações você puder fornecer, mais fácil será para nós reproduzir e corrigir o problema.
- Inclua as etapas a seguir com cada problema.

  - Etapas reproduzíveis (1... 2... 3...) e o que você esperava versus o que você experimentou.
  - Imagens, animações ou um link para um vídeo. Imagens e animações ilustram as etapas de reprodução, mas _não_ as substituem.
  - Conforme apropriado, um trecho de código que demonstra o problema ou um link para um repositório de código que podemos facilmente obter em nossa máquina para recriar o problema.

- Lembre-se de realizar as seguintes etapas:

  - Pesquise para ver se existe uma duplicata. Nesse caso, vote no problema existente, fornecendo comentários adicionais ou esclarecimentos, conforme necessário.
  - Recrie o problema depois de desabilitar todas as extensões. Se você achar que o problema é causado por uma extensão que você instalou, execute um problema na extensão, respectivamente.
  - Simplifique seu código em relação ao problema para que possamos isolá-lo de uma forma melhor.

Mesmo com problemas que incluem detalhes avançados, talvez não seja possível reproduzir o problema e pode pedir mais informações!

## <a name="managing-problem-reports"></a>Gerenciando relatórios de problemas

A separação de um problema é um processo de várias etapas que é feito de forma colaborativa na equipe de recursos. A triagem geralmente leva uma semana, mas pode levar mais tempo. O objetivo da separação é fornecer uma compreensão clara do que acontecerá com o seu problema. Por exemplo, após a triagem, você saberá se planejamos corrigir seu problema ou aguardar mais comentários da Comunidade.

Depois de relatar um problema, os estados indicam onde seus envios estão no seu ciclo de vida. À medida que as equipes de produtos do Visual Studio revisam seus comentários, elas as definem com um estado apropriado. Acompanhe o progresso dos relatórios de problemas referenciando os [Estados e as perguntas frequentes do problema](./report-a-problem.md).

### <a name="prioritizing-which-issues-to-fix"></a>Priorizando quais problemas corrigir

Não é possível corrigir todo o problema relatado. Alguns são muito caros de corrigir, alguns podem retornar outras áreas de recursos e alguns podem ter um impacto muito baixo. Entendemos que isso pode ser desapontador se você já levou algum tempo para nos enviar um relatório de problemas. Todos estamos lá, seja nesse projeto ou em outros que contribuímos. Se um problema foi fechado e você sentir que o motivo pelo qual não foi satisfatório, poderá esclarecer seu caso de uso e solicitar que o problema seja reativado para outro passo. Neste ponto, poderemos solicitar mais informações.

### <a name="missing-important-information"></a>Informações importantes ausentes

Quando faltam informações importantes no problema, atribuímos o estado de _mais informações_ . Comentamos o problema com as informações específicas de que precisamos e você receberá uma notificação por email. Se não recebermos as informações dentro de sete dias, enviaremos um lembrete. Depois disso, fechamos o tíquete após 14 dias de inatividade.

### <a name="other-product"></a>Outro produto

Às vezes, ao relatar um problema, ele se torna causado por outro produto e não pelo Visual Studio. Pode ser outro aplicativo relacionado ou uma extensão. 

Quando isso acontecer, fecharemos o problema e solicitaremos que você o abra com o outro produto. Aqui estão alguns locais comuns para arquivar esses problemas:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Suporte à assinatura do Visual Studio](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Informações adicionais

- [Como aumentar as chances de um problema de desempenho ser corrigido](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Solucionar problemas e criar logs para problemas do MSBuild](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Gerenciando sugestões de recursos

As sugestões de recursos são um meio de comunicação entre nós e os membros da comunidade de desenvolvedores. Tecnicamente, poderíamos manter todas as solicitações de recursos abertas para sempre. Mas manter os problemas abertos reduziria a visibilidade da Comunidade no status real de um recurso. Portanto, fechamos as solicitações de recurso que não abordaremos e atribuíremos recursos que nós podemos abordar ao rótulo de _revisão_ .

Se você sugeriu um recurso, talvez esteja desapontado que não planejamos atender à sua solicitação. Compreendemos isso. Todos nós já estamos lá neste projeto ou outros que contribuímos. Portanto, tenha certeza de que você adorará todas as suas entradas. Não pegue ataque pessoais quando fecharmos ou atribuímos o rótulo _sob revisão_ à sua sugestão. Se você sentir que sua sugestão de recursos merece estar aberta, esclareça o caso de uso e fale conosco ou reúna mais votos.

Em nosso processo de tomada de decisão, examinamos as seguintes características sobre a sugestão de recurso:

- Ele corresponde à nossa direção geral do produto?
- Podemos criar e mantê-lo?
- Ele se alinha com nossa estratégia geral de [roteiro](/visualstudio/productinfo/vs-roadmap) ?
- Ele tem suporte da Comunidade, conforme indicado por votos e comentários?
- Nós adoramos isso, mesmo com baixo suporte da Comunidade?

Quando não for possível responder "Sim" a qualquer uma dessas perguntas, vamos fechá-la. Mas, muitas vezes, a sugestão permanecerá aberta como _sob análise_ para reunir mais comentários da Comunidade.

Se uma sugestão não corresponder à nossa direção geral do produto, nós a fecharemos como *fora do escopo*. Por exemplo, poderemos ter investimentos semelhantes em outros membros da família de produtos Visual Studio. Ou o recurso sugerido pode ser relevante apenas para algumas pessoas, tornando uma extensão mais adequada para fornecê-la.

Acompanhe o progresso de sua sugestão de recurso referenciando os [Estados de sugestão e as perguntas frequentes](./report-a-problem.md).

## <a name="discussion-etiquette"></a>Etiqueta de discussão

Para manter a conversa clara e transparente, limite a discussão para o inglês e mantenha as coisas relevantes para o problema. Seja considerem para outras pessoas e sempre tente ser educado e Professional.

Para obter mais informações, consulte o [código de conduta da Comunidade da Microsoft](https://answers.microsoft.com/en-us/page/codeofconduct).

Quaisquer violações no etiqueta de discussão podem levar à remoção do comentário e, eventualmente, à proibição do usuário.

## <a name="data-privacy"></a>Privacidade dos dados

Comentários e respostas são visíveis publicamente, mas todos os arquivos anexados são compartilhados de forma privada somente com a Microsoft. Essa visibilidade é benéfica porque permite que toda a Comunidade Veja os problemas e soluções encontrados por outros usuários. Se você estiver preocupado com a privacidade de seus dados ou identidade, terá opções. Leia mais sobre a [privacidade de dados da comunidade de desenvolvedores](./developer-community-privacy.md).

## <a name="next-steps"></a>Próximas etapas

Acesse a comunidade de [desenvolvedores do Visual Studio](https://aka.ms/feedback/suggest?space=8) para relatar problemas, sugerir recursos ou navegar pelos tíquetes existentes. Aproveite!
