---
title: Notificações e Progresso para O Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699876"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notificações e progresso do Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>Sistemas de notificação

### <a name="overview"></a>Visão geral
 Existem várias maneiras de informar o usuário sobre o que está acontecendo no Visual Studio sobre suas tarefas de desenvolvimento de software.

 Ao implementar qualquer tipo de notificação:

- **Mantenha o número de notificações para o** número mínimo efetivo. As mensagens de notificação devem ser aplicadas à maioria dos usuários do Visual Studio ou aos usuários de uma área específica de recursos/recursos. O uso excessivo de notificações pode desviar o usuário ou diminuir a facilidade percebida de uso do sistema.

- **Certifique-se de que você está apresentando mensagens claras e acionáveis** que o usuário pode usar para invocar o contexto apropriado para fazer escolhas mais complexas e tomar medidas adicionais.

- **Apresente mensagens síncronas e assíncronas apropriadamente.** Notificações síncronas indicam que algo precisa de atenção imediata, como quando um serviço web falha ou uma exceção de código é lançada. O usuário deve ser informado dessas situações imediatamente de forma que exija sua entrada, como em um diálogo modal. Notificações assíncronas são as que o usuário deve saber, mas não é necessário agir imediatamente, como quando uma operação de compilação é concluída ou uma implantação de site termina. Essas mensagens devem ser mais ambiente e não interromper o fluxo de tarefas do usuário.

- **Use diálogos modais somente quando necessário para evitar que o usuário tome mais medidas** antes de reconhecer a mensagem ou tomar uma decisão apresentada no diálogo.

- **Remova as notificações ambientais quando elas não estiverem mais válidas.** Não exija que o usuário descarte uma notificação se já tiver tomado medidas para resolver o problema sobre o que foi notificado.

- **Esteja ciente de que as notificações podem levar a falsas correlações.** Os usuários podem acreditar que uma ou mais de suas ações desencadearam uma notificação quando, na verdade, não havia relação causal. Fique claro na mensagem de notificação sobre o contexto, o gatilho e a fonte da notificação.

### <a name="choosing-the-right-method"></a>Escolhendo o método certo
 Use esta tabela para ajudá-lo a escolher o método certo para notificar o usuário de sua mensagem.

|Método|Use|Não usar|
|------------|---------|----------------|
|[Diálogos de mensagem de erro modal](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Use quando uma resposta do usuário for necessária antes de prosseguir.|Não use quando não houver necessidade de bloquear o usuário e interromper seu fluxo. Evite usar diálogos modais se for possível mostrar a mensagem de outra forma, menos intrusiva.|
|[Barra de status do IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Use quando houver informações texucríticas ambientais sobre o status de um processo.|Não use sozinho. Melhor usado em conjunto com outro mecanismo de feedback.|
|[Barra de informações incorporada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Em uma janela de ferramenta ou janela de documento, use para notificar o progresso, o estado de erro, os resultados e/ou as informações acionáveis.|Não use se as informações não forem relevantes para o local onde a barra de informações está colocada.<br /><br /> Não use fora de uma janela de documento/ferramenta.|
|[Alterações no cursor do mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Pode ser usado para notificar que um processo está acontecendo. Também usado para notificar que há uma alteração de estado no mouse, como quando arrastar/soltar está em andamento ou que o cursor do mouse está em um determinado modo, como o modo de desenho.|Não use para alterações de progresso curto ou se a vibração do cursor é provável (por exemplo, quando ligada a partes de um processo de execução mais longo em vez de todo o processo).|
|[Indicadores de progresso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Use quando precisar relatar o progresso (por tempo determinado ou indeterminado). Existem uma variedade de tipos de indicadores de progresso e uso específico para cada um. Ver [indicadores de progresso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Janela de Notificações do Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|A janela Notificações não é publicamente extensível. No entanto, ele é usado para comunicar uma série de mensagens sobre o Visual Studio, incluindo problemas críticos com sua licença e notificações informacionais de atualizações para o Visual Studio ou para pacotes.|Não use para outros tipos de notificações.|
|[Lista de erros](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Quando o problema se relaciona diretamente com a solução aberta atualmente do usuário com um problema (erro/aviso/informação), ele pode precisar tomar medidas sobre o código.<br /><br /> Isso incluiria, por exemplo:<br /><br /> - Mensagens de compilador (erro/aviso/informação)<br /><br /> - Code Analyzer/Mensagens de diagnóstico sobre o código<br /><br /> - Construir mensagens<br /><br /> Pode ser apropriado para problemas relacionados com os arquivos de projeto ou solução, mas considere uma indicação do Solution Explorer primeiro.|Não use para itens que não tenham qualquer relação com o código de solução aberta do usuário.|
|Notificações do editor: Lâmpada|Use quando tiver uma correção disponível para remediar um problema que existe no arquivo aberto.<br /><br /> Observe que a Lâmpada também deve ser usada para hospedar Ações Rápidas que são tomadas no código do usuário sob demanda, como refatorações, mas nesse caso não aparecerá "estilo de notificação".|Não use para itens que não tenham qualquer relação com o arquivo aberto.|
|Notificações do editor: Squiggles|Use para alertar o usuário sobre um problema com um determinado período de seu código aberto (por exemplo, um rabisco vermelho para erros).|Não use para itens que não se relacionam com um determinado período de seu código aberto.|
|[Barras de status incorporadas](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Use para fornecer status relacionado ao conteúdo ou processo dentro do contexto de uma janela de ferramenta específica, janela de documento ou janela de diálogo.|Não use para notificações gerais de produtos, processos ou itens que não tenham qualquer relação com o conteúdo dentro da janela específica.|
|[Notificações da bandeja do Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Use para superfície notificações para processos fora do proc ou aplicativos complementares.|Não use para notificações relevantes para o IDE.|
|[Bolhas de notificação](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Use para notificar um processo remoto ou alterar **fora** do IDE.|Não use como meio notificar o usuário de processos **dentro** do IDE.|

### <a name="notification-methods"></a>Métodos de notificação

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Diálogos de mensagem de erro modal
 Uma caixa de diálogo de mensagem de erro modal é usada para exibir uma mensagem de erro que requer a confirmação ou ação do usuário.

 ![Mensagem de erro modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Uma mensagem de erro modal alertando o usuário de uma seqüência de conexão inválida para um banco de dados**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>Barra de status do IDE
 A probabilidade de os usuários notarem o texto da barra de status se correlaciona com sua experiência de computador e experiência específica com a plataforma Windows. A base de clientes do Visual Studio tende a ser experimentada em ambas as áreas, embora mesmo usuários experientes do Windows possam perder mudanças na barra de status. Portanto, a barra de status é melhor usada para fins informativos ou como uma sugestão redundante para informações apresentadas em outros lugares. Qualquer tipo de informação crítica que o usuário deve resolver imediatamente deve ser fornecida em um diálogo ou na janela da ferramenta Notificações.

 A barra de status do Visual Studio foi projetada para permitir que vários tipos de informações sejam exibidas. Ele é dividido em regiões para feedback, designer, barra de progresso, animação e cliente.

 A região de feedback e a região do designer são sempre visíveis. A barra de progresso e as regiões de animação são sempre dinâmicas e baseadas no contexto do usuário. A região do designer tem uma largura estática determinada pelo comprimento da string que é puxada de um recurso de acompanhamento para a mensagem de texto. Isso permite que a localização redimensione a largura sem exigir uma alteração de código. Para inglês, a largura desta string é de aproximadamente 220 pixels. A região do designer se comportará normalmente e a região de feedback absorverá o espaço restante.

 A barra de status também é colorida para adicionar interesse visual e valor funcional, comunicando várias alterações de estado IDE, como quando o IDE está no modo de depuração.

 ![Alterações de cor da barra de status do IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Cores da barra de status do IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Barra de informações incorporada
 Uma barra de informações pode ser usada no topo de uma janela de documento ou janela de ferramenta para informar o usuário de um estado ou condição. Ele também pode oferecer comandos para que o usuário possa ter uma maneira de agir facilmente. A Infobar é um controle padrão de shell. Evite criar o seu próprio, que agirá e parecerá inconsistente com os outros no IDE. Consulte [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) para obter detalhes de implementação e orientação de uso.

 ![Barra de informações incorporada](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Uma barra de informações embutida em uma janela de documento, alertando o usuário de que o IDE está no modo de depuração histórica e o editor não responderá da mesma forma que no modo de depuração padrão.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Alterações no cursor do mouse
 Ao alterar o cursor do mouse, use cores vinculadas ao serviço VSColor e que já estejam associadas ao cursor. Alterações no cursor podem ser usadas para indicar uma operação em andamento, bem como para as zonas de impacto onde o usuário está pairando sobre um alvo que pode ser arrastado, jogado sobre ou usado para selecionar um objeto.

 Use o cursor do mouse ocupado/wait somente quando todo o tempo de CPU disponível for reservado para uma operação, impedindo que o usuário expresse qualquer entrada adicional. Na maioria dos casos, com aplicativos bem escritos usando multithreading, momentos em que os usuários são impedidos de fazer outras operações devem ser raros.

 Tenha em mente que as alterações do cursor são úteis como uma sugestão redundante para informações apresentadas em outros lugares. Não confie em uma mudança de cursor como a única maneira de se comunicar com o usuário especialmente ao tentar transmitir algo que é crítico que o usuário deve abordar.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Indicadores de progresso
 Os indicadores de progresso são importantes para dar ao usuário feedback durante processos que levam mais de alguns segundos para serem concluídos. Os indicadores de progresso podem ser mostrados no local (perto do ponto de lançamento da ação em andamento), em uma barra de status incorporada, em um diálogo modal ou na barra de status do Visual Studio. Siga as orientações em [Progress indicadores](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) sobre seu uso e implementação.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Janela de Notificações do Visual Studio
 A janela Visual Studio Notifications notifica os desenvolvedores sobre licenciamento, ambiente (Visual Studio), extensões e atualizações. Os usuários podem descartar notificações individuais ou optar por ignorar certos tipos de notificações. A lista de notificações ignoradas é gerenciada em uma página **De opções de > Ferramentas.**

 A janela Notificações não é extensível no momento.

 ![Janela de Notificações do Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Janela da ferramenta Visual Studio Notifications**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>Lista de erros
 Uma notificação dentro da lista de erros indica erros e avisos que ocorreram durante o processo de compilação e ou construção, e permite que o usuário navegue em código para esse erro de código específico.

 ![Lista de erros](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Lista de erros no Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Barras de status incorporadas
 Como a barra de status do IDE é dinâmica, com seu contexto de região do cliente definido para a janela ativa do documento e atualização de informações sobre o contexto do usuário e/ou respostas do sistema, é difícil manter uma exibição contínua de informações ou dar status em processos assíncronos de longo prazo. Por exemplo, a barra de status do IDE não é apropriada para notificações de resultados de execução de testes para várias seleções de itens e/ou imediatamente acionáveis. É importante reter essas informações de status no contexto da janela de documento ou ferramenta onde o usuário faz uma seleção ou inicia um processo.

 ![Barra de status incorporada](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barra de status incorporada no Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Notificações da bandeja do Windows
 A área de notificação do Windows está ao lado do relógio do sistema na barra de tarefas do Windows. Muitos utilitários e componentes de software fornecem ícones nesta área para que o usuário possa obter um menu de contexto para tarefas em todo o sistema, como alterar a resolução da tela ou obter atualizações de software.

 As notificações em nível de ambiente devem ser fornecidas no centro de Notificações do Visual Studio, não na área de notificação do Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Bolhas de notificação
 Bolhas de notificação podem aparecer como informacionais dentro de um editor/designer ou como parte da área de Notificação do Windows. O usuário percebe essas bolhas como problemas que podem resolver mais tarde, o que é um benefício para notificações não críticas. Bolhas são inadequadas para informações críticas que o usuário deve resolver imediatamente. Se você usar bolhas de notificação no Visual Studio, siga a [orientação](/windows/desktop/uxguide/mess-notif)do Windows Desktop para bolhas de notificação .

 ![Bolha de notificação](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Bolha de notificação na área de notificação do Windows usada para o Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Indicadores de progresso

### <a name="overview"></a>Visão geral
 Os indicadores de progresso são uma parte importante de um sistema de notificação para dar feedback ao usuário. Eles dizem ao usuário quando os processos e operações serão concluídos. Os tipos de indicadores familiares incluem barras de progresso, cursores giratórios e ícones animados. O tipo e a colocação de um indicador de progresso depende do contexto, incluindo o que está sendo relatado e quanto tempo o processo ou operação levará para ser concluído.

#### <a name="factors"></a>Fatores
 Para determinar qual tipo de indicador é apropriado, você precisa determinar os seguintes fatores.

1. **Tempo:** tempo que a operação levará

2. **Modalidade:** se a operação é modal para o ambiente (bloqueia a ui até que o processo esteja concluído)

3. **Persistente/Transitório:** se o resultado final do progresso precisa ser relatado e/ou visível posteriormente

4. **Determinado/indeterminado:** se o tempo final da operação e o progresso podem ser calculados

5. **Localização gráfica/textual:** se o progresso ou processo é capturado em linha, no corpo de uma mensagem ou em um controle específico, como o controle da árvore

6. **Proximidade:** se o progresso deve estar próximo da UI a que está relacionado. (Por exemplo, pode estar na barra de status, que pode estar longe, ou tem que estar perto do botão que iniciou o processo?)

#### <a name="determinate-progress"></a>Progresso determinado

|Tipo de progresso|Quando e como usar|Observações|
|-------------------|-------------------------|-----------|
|Barra de progresso (determinada)|Duração esperada de >5 segundos.<br /><br /> Pode incluir descrição textual dos detalhes do processo.|**NÃO** incorpore texto em animação.|
|Barra|Mensagens associadas à ui contextual. Ver [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Pode incluir descrição textual dos detalhes do processo.|**NÃO use** várias infobarras quando precisar indicar vários processos. Use barras de progresso empilhadas em vez disso.|
|Janela de saída|Notificação transitória: processo de nível de aplicativo que o usuário deseja **revisar** detalhes após a conclusão.|**NÃO use** se o usuário precisar consultar os dados mais tarde.|
|Arquivo de log|Emparelhado com uma notificação intransiente nos casos em que é importante **salvar** detalhes após a conclusão.||
|Barra de status|Notificação transitória: processo de nível de aplicativo do que o usuário **não precisará** de detalhes após a conclusão.<br /><br /> Inclui uma barra de progresso incorporada.<br /><br /> Pode incluir descrição textual dos detalhes do processo.||

#### <a name="indeterminate-progress"></a>Progresso indeterminado

|Tipo de progresso|Quando e como usar|Observações|
|-------------------|-------------------------|-----------|
|Barra de progresso (indeterminada)|Duração esperada de >5 segundos.<br /><br /> Pode incluir descrição textual dos detalhes do processo.|**NÃO** incorpore texto em animação.|
|Formigas (pontilhados horizontais animados)|Ida e volta para o servidor.<br /><br /> Colocado perto do ponto de contexto em cima do recipiente pai.|**NÃO use** se não for pai por um recipiente inteiro.|
|Spinner (anel de progresso)|Processo associado à ui contextual, ou onde o espaço é uma consideração.<br /><br /> Pode incluir descrição textual dos detalhes do processo.||
|Barra|Mensagens associadas à ui contextual. Ver [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**NÃO use** várias infobarras quando precisar indicar vários processos. Use barras de progresso empilhadas em vez disso.|
|Janela de saída|Notificação transitória: processo de nível de aplicativo que o usuário deseja **revisar** detalhes após a conclusão.|**NÃO use** para informações que precisam persistir ao longo das sessões.|
|Arquivo de log|Emparelhado com uma notificação intransiente nos casos em que é importante **salvar** detalhes após a conclusão.||
|Barra de status|Notificação transitória: processo de nível de aplicativo do que o usuário **não precisará** de detalhes após a conclusão.<br /><br /> Inclui barra de progresso incorporada.<br /><br /> Pode incluir descrição textual dos detalhes do processo.||

### <a name="progress-indicator-types"></a>Tipos de indicadores de progresso

#### <a name="progress-bars"></a>Barras de progresso

##### <a name="indeterminate"></a>Indeterminado
 ![Barra de progresso indeterminada](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Barra de progresso indeterminada**

 "Indeterminado" significa que o progresso geral de uma operação ou processo não pode ser determinado. Use barras de progresso indeterminadas para operações que requerem uma quantidade de tempo ilimitada ou que acessem um número desconhecido de objetos. Use uma descrição textual para acompanhar o que está acontecendo. Use tempos limite para dar limites às operações baseadas no tempo. Barras de progresso indeterminadas usam animações para mostrar que o progresso está sendo feito, mas não fornecem outras informações. Não escolha uma barra de progresso indeterminada baseada apenas na possível falta de precisão.

##### <a name="determinate"></a>Determinado
 ![Barra de progresso determinada](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Barra de progresso determinada**

 "Determinado" significa que uma operação ou processo requer uma quantidade limitada de tempo, mesmo que essa quantidade de tempo não possa ser prevista com precisão. Indica claramente a conclusão. Não deixe uma barra de progresso ir para 100% a menos que a operação tenha sido concluída. A animação da barra de progresso deserda move-se da esquerda para a direita de 0 a 100%.

 Nunca mova o indicador de progresso para trás durante uma operação. A barra deve avançar continuamente quando a operação começar e atingir 100% quando terminar. O objetivo da barra de progresso é dar ao usuário uma ideia de quanto tempo toda a operação leva, independentemente de quantas etapas estão envolvidas.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Relatórios simultâneos (barras de progresso empilhadas)
 Se uma operação levará muito tempo - talvez vários minutos - então duas barras de progresso podem ser usadas, uma que mostra progresso geral para uma operação e outra para a progressão da etapa atual. Por exemplo, se um programa de configuração estiver copiando muitos arquivos, então uma barra de progresso pode ser usada para indicar quanto tempo todo o processo leva enquanto um segundo pode indicar qual porcentagem do arquivo ou diretório atual está sendo copiado. Não informe mais de cinco operações ou processos simultâneos usando barras de progresso empilhadas. Se você tiver mais de cinco operações ou processos simultâneos para relatar, use um diálogo modal com um botão Cancelar e informe os detalhes de progresso à Janela de Saída.

##### <a name="textual-descriptions"></a>Descrições texuais
 Use uma descrição textual para acompanhar o que está acontecendo e o tempo estimado para conclusão. Se é impossível determinar quanto tempo uma operação levará, então uma escolha melhor para dar feedback pode ser um ícone animado em vez de uma barra de progresso.

 O Visual Studio fornece uma barra de progresso padrão na barra de status que pode ser usada por qualquer produto integrado ao Visual Studio. Para descrições texudas do que está acontecendo enquanto a barra de progresso é animada, o texto da barra de status pode ser atualizado.

#### <a name="other-progress-indicators"></a>Outros indicadores de progresso

##### <a name="ants-animated-horizontal-dots"></a>Formigas (pontilhados horizontais animados)
 ![Formigas do progresso](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Formigas", pontificas horizontais animadas, fornecem uma referência visual para um processo indeterminado de servidor de ida e volta.

##### <a name="spinner-progress-ring"></a>Spinner (anel de progresso)
 ![Rotador de progresso](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 O spinner (também conhecido como "anel de progresso") é um indicador de progresso indeterminado usado principalmente em relação à ui contextual. Exibir um spinner próximo ao seu conteúdo relacionado, como um cabeçalho de categoria textual, mensagens ou controle.

##### <a name="cursor-feedback"></a>Feedback do cursor
 Para operações que levam entre 2-7 segundos, forneça feedback do cursor. Normalmente, isso significa usar o cursor de espera fornecido pelo sistema operacional. Para obter orientação, consulte o artigo do MSDN [Cursors.Wait Property](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>Locais do indicador de progresso

##### <a name="status-bar"></a>Barra de status
 A barra de status dá ao seu aplicativo um lugar para exibir mensagens e informações úteis ao usuário sem interromper o trabalho do usuário. Normalmente exibido na parte inferior de uma janela, o status para o progresso será um painel de ponta de ferramenta que inclui uma mensagem sobre a medida do progresso em combinação com um indicador de barra de progresso.

 ![Barra de status com barra de progresso](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barra de status com barra de progresso**

 ![Barra de status com mensagens](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Barra de status com descrição textual**

##### <a name="infobar"></a>Barra
 Semelhante à barra de status, a barra de informações fornece notificação contextual e mensagens, que também podem ser emparelhadas com indicadores de progresso indeterminados, como a barra de progresso ou o spinner. A barra de informações não deve fornecer progresso de nível granular ou indicação de progresso determinado. Ver [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Barra de informações com barra de progresso e mensagens](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Barra de informações com barra de progresso e descrição textual**

 ![Barra de informações dentro de uma janela](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Embutido
 A indicação de progresso inline pode ser representada por qualquer um dos tipos de carregadores de progresso. Normalmente, o indicador de progresso é emparelhado com mensagens, mas isso não é um requisito.

 ![Rotador de progresso inline](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner combinado com descrição textual**

 ![Barras de progresso empilhadas inline](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Determine barras de progresso empilhadas**

 ![Mensagens de progresso inline](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Texto inline do Server Explorer: Refrescante...**

##### <a name="tool-windows"></a>Janelas da ferramenta
 A indicação de progresso global é representada por uma barra de progresso indeterminada posicionada diretamente abaixo da barra de ferramentas.

 ![Barra de progresso indeterminada global](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Barra de progresso indeterminada do Team Explorer global**

##### <a name="dialogs"></a>Diálogos
 Os diálogos podem conter qualquer um dos tipos de carregador de progresso. Os indicadores de progresso podem ser emparelhados com mensagens, bem como combinados com múltiplos níveis de indicação de progresso para representar granulares e subprocessos.

 ![Diálogo com vários tipos de indicadores de progresso](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Diálogo visual studio com processos simultâneos e vários tipos de indicadores de progresso**

 ![Diálogo com carregador de progresso e mensagens](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Diálogo visual studio com carregador de progresso e comando de mensagens em linha**

##### <a name="document-well"></a>Documento bem
 O documento bem pode exibir vários tipos de carregadorde progresso em combinação com controles.

 ![Mensagens de progresso no documento bem](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Barra de progresso indeterminada abaixo da barra de ferramentas**

##### <a name="output-window"></a>Janela de saída
 A janela Saída é apropriada para lidar com a progressão do processo e o status de progresso contínuo através de mensagens texuais inline. Você deve usar a barra de status juntamente com qualquer relatório de progresso da janela de saída.

 ![Mensagens de progresso na janela de saída](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Janela de saída com status de processo em andamento e mensagens de espera**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>Infobares

### <a name="overview"></a>Visão geral
 As barras de infodo dão ao usuário um indicador próximo ao seu ponto de atenção e o uso do controle de infobar compartilhado garante consistência na aparência visual e interação.

 ![Barra](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Infobares no Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Usos apropriados para uma barra de informações

- Para dar ao usuário uma mensagem não bloqueada, mas importante relevante para o contexto atual

- Para indicar que a UI está em um determinado estado ou condição que carrega algumas implicações de interação, como a depuração histórica

- Para notificar o usuário que o sistema detectou problemas, como quando uma extensão está causando problemas de desempenho

- Para fornecer ao usuário uma maneira de agir facilmente, como quando o editor detecta que um arquivo tem guias e espaços mistos

##### <a name="do"></a>Fazem:

- Mantenha o texto da mensagem da barra de informações curto e ao ponto.

- Mantenha o texto em links e botões sucintas.

- Certifique-se de que as opções de "ação" que você fornece aos usuários são mínimas, mostrando apenas as ações necessárias.

##### <a name="dont"></a>Não:

- Use uma barra de informações para oferecer comandos padrão que devem ser colocados em uma barra de ferramentas.

- Use uma barra de informações no lugar de um diálogo modal.

- Crie uma mensagem flutuante fora de uma janela.

- Use várias barras de infoem em vários locais dentro da mesma janela.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Vários infobares podem aparecer ao mesmo tempo?
 Sim, vários infobares podem aparecer ao mesmo tempo. Eles serão exibidos por ordem por ordem por ordem por ordem, com a primeira barra de informações exibida em cima e infobars adicionais mostrando abaixo.

 O usuário verá um máximo de três infobarras por vez, após o qual, se mais infobarras estiverem disponíveis, a região da infobar se tornará rolável.

### <a name="creating-an-infobar"></a>Criando uma barra de informações
 A barra de informações tem quatro seções, da esquerda para a direita:

- **Ícone:** É aqui que você adicionaria qualquer ícone que deseja exibir para a barra de informações, como um ícone de aviso.

- **Texto:** Você pode adicionar texto para descrever o cenário/situação em que o usuário está, juntamente com links dentro do texto, se necessário. Lembre-se de manter o texto sucinto.

- **Ações:** Esta seção deve conter links e botões para ações que o usuário pode tomar em sua barra de informações.

- **Botão fechar:** A última seção à direita pode ter um botão de fechar.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Criando uma barra de informações padrão no código gerenciado
 A classe InfoBarModel pode ser usada para criar uma fonte de dados para uma barra de informações. Use um desses quatro construtores:

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 Aqui está um exemplo que cria um InfoBarModel com algum texto com um hiperlink, um botão de ação e um ícone.

 ![Infobar com hiperlink](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>Criando uma barra de informações padrão em código nativo
 Implemente a interface IVsInfoBar para fornecer uma barra de informações a partir do código nativo.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtendo uma uielement de infobar de uma barra de informações
 A implementação InfoBarModel ou IVsInfoBar são modelos de dados que devem ser transformados em um UIElement para serem mostrados na ui. Um UIElement pode ser recuperado com o serviço SVsInfoBarUIFactory/IVsInfoBarUIFactory.

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>Posicionamento
 As barras de infot podem ser mostradas em um ou mais dos seguintes locais:

- Janelas da ferramenta

- Dentro de uma guia de documentos

> [!IMPORTANT]
> É possível posicionar uma barra de informações para dar uma mensagem sobre o contexto global. Isso apareceria bem entre as barras de ferramentas e o documento. Isso não é recomendado porque causa problemas com o "salto e empurrão" do IDE e deve ser evitado, a menos que seja absolutamente necessário e apropriado.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Colocando uma barra de informações em um ToolWindowPane
 O método ToolWindowPane.AddInfoBar(IVsInfoBar) pode ser usado para adicionar uma barra de informações a uma janela de ferramenta. Esta API pode adicionar um IVsInfoBar (do qual o InfoBarModel é uma implementação padrão) ou um IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Colocar uma barra de informações em um documento ou não-ToolWindowPane
 Para colocar uma barra de informações em qualquer IVsWindowFrame, use a propriedade VSFPROPID_InfoBarHost para obter o IVsInfoBarHost para o quadro e, em seguida, adicione a barra de informações UIElement.

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>Colocando uma barra de informações na janela principal
 Para colocar uma barra de informações na janela principal, use o VSSPROPID_MainWindowInfoBarHost do serviço IVsShell para obter o IVsInfoBarHost da janela principal e, em seguida, adicione a barra de informações UIElement a ele.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Saberei quando o usuário agirá na minha barra de informações?
 Sim, retornaremos todas as ações do evento ao autor da barra de informações. Cabe então ao autor da infobar agir no IDE com base na seleção do usuário na barra de informações. As infobarras serão automaticamente removidas do host cujo botão Fechar foi clicado, mas é necessário trabalho adicional se outras barras de infobar precisarem ser removidas após o fechamento. A telemetria também precisará ser registrada de forma independente por cada infobar.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recebendo eventos de infobar em um ToolWindowPane
 ToolWindowPane tem dois eventos para infobars. O evento InfoBarClosed é levantado quando uma barra de informações no ToolWindowPane é fechada. O evento InfoBarActionItemClicked é levantado quando um hiperlink ou botão dentro da barra de informações é clicado.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Recebendo eventos de infobar diretamente do UIElement
 IVsInfoBarUIElement.Advise pode ser usado para se inscrever em eventos diretamente do UIElement de uma barra de informações. A implementação do IVsInfoBarUIEvents permitirá que o autor receba eventos próximos e cliques.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>Validação de erros
 Quando um usuário insere informações que não são aceitáveis, como quando um campo necessário é ignorado ou quando os dados são inseridos no formato incorreto, é melhor usar validação de controle ou feedback perto do controle em vez de usar uma caixa de diálogo de erro pop-up de bloqueio.

### <a name="field-validation"></a>Validação do campo
 A validação de formulário e campo consiste em três componentes: um controle, um ícone e uma dica de ferramenta. Embora vários tipos de controles possam usar isso, uma caixa de texto será usada como exemplo.

 ![Validação de campo &#40;&#41;em branco](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Se o campo for necessário, deve ** \<** haver um texto de marca d'água `Environment.ControlEditRequiredBackground`indicando>obrigatório e o fundo `Environment.ControlEditRequiredHintText`do campo deve ser amarelo claro (VSColor: ) e o primeiro plano deve ser cinza (VSColor: ):

 ![Validação de campo com rótulo "Obrigatório"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 O programa pode determinar que o controle está em um estado de *conteúdo inválido inserido* quando o foco é movido para outro controle ou quando o usuário clica em um botão de compromisso [OK] ou quando o usuário salva o documento ou formulário.

 Quando o estado de conteúdo inválido é determinado, um ícone aparece dentro do controle ou apenas ao lado dele. Uma dica de ferramenta descrevendo o erro deve aparecer no pairamento do ícone ou do controle. Além disso, uma borda de 1 pixel deve aparecer em torno do controle que está criando o estado inválido.

 ![Especificações do layout de validação de campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Especificações de layout para validação de campo**

#### <a name="acceptable-variations-for-icon-location"></a>Variações aceitáveis para localização de ícones
 Existem inúmeros casos únicos em que os usuários precisam ser informados sobre erros de validação. Considerando o tipo de controle e configuração da ui, escolha a colocação do ícone adequada à sua situação.

 ![Locais aceitáveis para localização de ícones](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Variações aceitáveis para locais de ícones de validação de campo**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validação que requer uma ida e volta para um servidor ou conexão de rede
 Em alguns casos, uma ida e volta ao servidor é necessária para verificar o conteúdo, e seria importante mostrar o progresso do usuário, os estados verificados e os erros. A figura abaixo mostra um exemplo deste caso e da ui recomendada.

 ![Validação envolvendo uma ida e volta para um servidor](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Validação envolvendo uma ida e volta para um servidor**

 Observe que deve ser fornecido espaço disponível adequado à direita do controle para acomodar o "Verificando..." e texto "Retry".

#### <a name="in-place-warning-text"></a>Texto de aviso no local
 Quando há espaço disponível para colocar a mensagem de erro perto do controle em um estado de erro, isso é preferível usar apenas a dica de ferramenta.

 ![Em&#45;local aviso](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Texto de aviso no local**

#### <a name="watermarks"></a>Marcas d' água
 Às vezes, um controle inteiro ou janela está em um estado de erro. Nesta situação, use uma marca d'água para indicar o erro.

 ![Marca d' água](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Validação de campo de marca d'água**
