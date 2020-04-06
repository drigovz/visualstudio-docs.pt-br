---
title: Ferramentas de Avaliação para O Estúdio Visual | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ae5ae2d3be49a797ff1d594aab4517efab53330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698426"
---
# <a name="evaluation-tools-for-visual-studio"></a>Ferramentas de avaliação para Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Lista de verificação de artesanato para Visual Studio
 Use esta lista de verificação para avaliar a qualidade da experiência do usuário para detalhes visuais e de interação.

### <a name="overview"></a>Visão geral

- Verifique se todos os comandos resultam em feedback que informa aos usuários que seus comandos foram realizados.

- Verifique se todos os elementos e controles de IU são visíveis em todos os temas e no modo De Alto Contraste.

- Verifique se a seleção inativa e ativa são sempre diferenciadas, tanto no modo padrão quanto no modo De Alto Contraste.

- Verifique se o foco é sempre visível e aparente.

### <a name="performance"></a>Desempenho

- Verifique se algum tipo de indicador "ocupado" é mostrado se um comando leva mais de um segundo para ser concluído.

- Verifique se um comando leva mais de 10 segundos para ser concluído, uma barra de progresso explícita, determinada (preferida) ou indeterminada, é exibida.

### <a name="ui-text"></a>Texto de UI

- Verifique se todos os rótulos são de sentença ou de título e que nenhum texto é totalmente minúsculo.

    ||Correto|Incorreto|
    |-|-------------|---------------|
    |**Texto de comando (todos)**|Caso da sentença:<br /><br /> **Nome do diretório:**|Nome do diretório:|
    |**Texto de botão (cliente)**|Caso do título:<br /><br /> **[ Definido como padrão ]**|DEFINIDO COMO PADRÃO|
    |**Texto de botão (on-line)**|Caso da sentença:<br /><br /> **[ Definido como padrão ]**||

- Verifique se todos os rótulos, exceto cabeçalhos e botões de grupo, terminam com um cólon e precedem o controle com o qual estão emparelhados.

- Verifique se botões, comandos e links de comando que iniciam a iu para capturar a entrada do usuário terminam em uma elipse **[...]**.

  Exemplos:

  - Um botão **[Avançado...]** em uma caixa de diálogo.

  - As opções de comando no menu Ferramentas **( Ferramentas > Opções**) não devem receber uma elipse, pois o lançamento do diálogo em si é a intenção do comando.

- Verifique se a ui não contém abreviaturas, exceto os termos padrão do setor. Por exemplo, nem HTML nem TCP/IP precisam ser explicitados, embora OOM (fora da memória) e PII (informações pessoalmente identificáveis) devam.

### <a name="keyboard-access"></a>Acesso pelo teclado

- Verifique se há uma maneira de realizar cada tarefa com o teclado. Geralmente isso é feito através do acesso ao teclado para cada controle, mas para algumas áreas altamente visuais, uma solução alternativa como ir para a exibição de código é aceitável.

- Verifique se você pode fazer a guia através de controles em uma ordem lógica (da esquerda para a direita e de cima para baixo). Embora esta seja uma prática recomendada para a maioria dos controles, nem todos os controles exigem essa abordagem. Por exemplo, verifique se os controles do botão de rádio estão em um grupo com uma única parada de guia.

- Verifique se todos os controles possuem rótulos e se cada rótulo tem um mnemônico (exceções incluem alguns controles não rotulados que podem seguir um controle rotulado na guia).

- Verifique se não há conflitos mnemônicos.

### <a name="fonts"></a>Fontes

- Verifique se todas as fontes (rosto, tamanho, cor) são usadas de forma consistente e mantêm a hierarquia.

- Verifique se todos os elementos de II usam o serviço de fonte do ambiente. (Ver [fontes e formatação para o Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Para verificar se o serviço está sendo usado, acesse **Ferramentas > Opções > Fontes e Cores**. Na lista de configurações, escolha A fonte de ambiente e altere a face da fonte para algo estilisticamente diferente (como Harrington ou Comic Sans) e defina o tamanho para 12 pt. Em seguida, clique em OK. Você pode precisar reiniciar o IDE, mas a maioria da ui mudará imediatamente. As áreas que não captam a alteração de fonte mesmo na reinicialização não estão usando a fonte do ambiente.

- Verifique se as fontes derivadas do serviço (por exemplo, texto em negrito ou ampliado) mantêm seu tamanho e formatação em relação ao texto "normal" quando o tamanho da fonte do ambiente é alterado.

- Verifique se não há bugs de recorte devido a fontes ampliadas. As fontes que são cortadas são provavelmente o resultado de controles de altura fixos ou recipientes de altura fixa.

### <a name="dialogs"></a>Diálogos

- Verifique se o título da caixa de diálogo é o mesmo que o comando que o lançou.

- Verifique se todos os controles padrão são consistentes com o sistema operacional: a cor de fundo é padrão e nenhum controle deve ter um estilo especial de remodelação que os faça parecer diferentes dos controles padrão.

- Verifique se as margens dentro do formulário devem ser de 12 pixels e devem parecer uniformes e consistentes.

- Verifique se as caixas de diálogo aparecem centradas na concha IDE ou na janela que as gerou.

- Quando útil, os diálogos devem ser resizáveis. Para diálogos que são redimensionáveis, verifique se, ao redimensionar, os controles apropriados devem redimensionar enquanto outras partes da caixa de diálogo permanecem constantes.

- Verifique se as caixas de diálogo resizáveis persistem em qualquer tamanho ajustado pelo usuário (tamanho, localização, expansão dos controles de diálogo e assim por diante).

- Verifique se não há ícone na barra de títulos.

- Verifique se não há botões Minimizar e Maximizar na barra de título.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Botões de operação de diálogo (somente VS Cliente)

- Verifique se os botões de operação estão nesta ordem: **OK,** **Cancele,** **Aplique**.

- Verifique se os botões **OK** e **Cancel** são o tamanho padrão: 75x23 pixels.

- Verifique se os botões **OK** e **Cancel** são de tamanho igual, independentemente do comprimento da corda.

- Se a etiqueta em um botão de operação exigir que o botão seja mais largo do que o padrão, verifique se o botão **cancelar** correspondente é de tamanho igual.

- Verifique se há um preenchimento de 6 pixels entre botões e controles associados.

- Verifique se os botões **OK** e **Cancel** não possuem mnemônicos (chaves de acesso definidas por uma letra sublinhada).

- Verifique se um botão (tipicamente **OK)** tem foco por padrão.

- Verifique se **esc** cancela a caixa de diálogo

- Verifique se **Enter** executa o botão padrão se o foco não estiver em um controle que processa Enter.

- Verifique se os botões **OK** e **Cancel** estão posicionados no canto inferior direito da caixa de diálogo. Em raras exceções, é aceitável que sejam empilhados verticalmente no canto superior direito.

- Verifique se a configuração vertical é usada apenas se outros botões estiverem em um alinhamento horizontal dentro da caixa de diálogo.

### <a name="control-standards"></a>Padrões de controle

#### <a name="general"></a>Geral

- Verifique se, quando possível, existem bons valores padrão para acelerar a interação do usuário e direcionar os usuários para um resultado seguro ou comum.

- Verifique se os controles padrão se comportam da mesma maneira para que os usuários saibam o que acontecerá com base na experiência anterior.

#### <a name="label-controls"></a>Controles de rótulos

- Verifique se cada controle tem um rótulo e que cada rótulo está visualmente emparelhado com seu controle (geralmente dentro de uma faixa de 4-6 pixels) e está mais próximo de seu controle correspondente do que de outros controles.

- Verifique se as etiquetas estão posicionadas à esquerda com a borda esquerda do controle se posicionada acima e centralizada horizontalmente, de modo que a linha de base da etiqueta esteja alinhada com a linha de base do texto de entrada se posicionada à esquerda.

- Verifique se vários controles de etiqueta e entrada empilhados estiverem posicionados à esquerda de um controle, as etiquetas estão niveladas para a esquerda e a uma distância igual da borda da caixa, nunca lave para a direita e uma distância igual dos controles. Os pares devem ser distribuídos uniformemente, a menos que precisem de espaçamento adicional para indicar o agrupamento.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Controles de entrada (caixas de texto e caixas de combinação)

- Verifique se, ao usar a fonte de ambiente padrão, a altura do display para caixas de texto, caixas de combinação e botões são todos de 23 pixels.

- Se o texto da dica for usado, verifique se a cor está definida para `Environment.ControlEditHintText` usar o serviço de cores.

- Se o campo for um campo necessário que deve ser identificado como tal, verifique:

  - que o fundo `Environment.ControlEditRequiredBackground` está definido para eo primeiro plano é definido para`Environment.ControlEditRequiredHintText`

  - que há um texto de sugestão dentro do controle que aparece como **"\<> obrigatório"**

#### <a name="button-controls"></a>Controles de botão

- Verifique se os botões têm um tamanho mínimo de 75x23 pixels, a menos que acomode texto mais longo.

- Verifique se os botões têm margens esquerda e direita de 3-5 pixels, bem como preenchimento para o conteúdo.

- É aceitável usar um pequeno botão quadrado com apenas uma elipse **[...]** nele em vez de um botão **[Procurar...]** (ou funcionalidade semelhante). Se usado, verifique se o botão tem 23x23 de tamanho.

- Se houver mais de um botão **[Procurar...]** em uma caixa de diálogo, verifique se a versão encurtada (somente elipsis **[...]**) é usada para todos.

- Verifique se os botões elipse **[...]** não possuem um mnemônico. Quando o foco estiver no controle de entrada ao lado dele, uma guia deve mover o foco para o botão elipse.

- Verifique se botões, comandos e links de comando que lançam a ui secundária que captura mais entrada de usuário devem terminar em uma elipse **[...]**.

#### <a name="hyperlinks"></a>Hiperlinks

- Verifique se um controle de hiperlink nunca pisca vermelho quando ativo. Este é um indicador de que o serviço de cores não está sendo usado

- Verifique se as cores VS usadas são:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Verifique se os hiperlinks aparecem azuis sem sublinhar, a menos que seja incorporado em um parágrafo.

#### <a name="check-boxes"></a>Caixas de seleção

- Se uma caixa de seleção tiver texto de várias linhas, verifique se a caixa está alinhada com a primeira linha de texto, não centrada verticalmente em todas as linhas.

- Verifique se as caixas de seleção sempre indicam uma escolha binária e não naveguem pelo usuário ou abrem novas janelas ou páginas.

- Se uma caixa de seleção apresentar uma opção relacionada a um controle de entrada, verifique se ela está posicionada à esquerda e muito próxima sob esse controle para indicar sua relação.

- Verifique se uma caixa de seleção **nunca** é usada como um meio para ativar todo o conteúdo de uma caixa de diálogo ou página.

#### <a name="group-boxes"></a>Caixas de grupo

- Verifique se uma caixa de diálogo não contém uma única caixa de grupo dentro dela que contenha todo o conteúdo da caixa de diálogo.

- Verifique se há pelo menos dois controles dentro de cada caixa de grupo.

- Raramente deve haver mais de duas caixas de grupo em um diálogo.

- Verifique se não há caixas de grupo aninhadas.

### <a name="icons"></a>Ícones

- Verifique se os ícones aparecem corretamente invertidos quando no tema escuro.

- Verifique se todos os ícones são baseados em conceitos principais.

- Verifique se cada ícone é distinto, fácil de reconhecer e não contém mais de dois conceitos (sem modificador de status/linguagem).

- Verifique se o ícone de base aparece centrado no espaço.

- Verifique se todos os ícones se parecem legíveis no modo De Alto Contraste.

- Verifique se qualquer cor usada está alinhada com os padrões de uso de cores.

- Verifique se não há halos (bordas) em torno de ícones. (Se estiver presente, o halo deve corresponder à cor de fundo da ui adjacente).

### <a name="touch-enabled-ui"></a>UI ativada por toque

- Verifique se os controles interativos são grandes o suficiente para serem facilmente tocáveis - **mínimos 23x23 pixels** de tamanho

- Verifique se os controles mais usados têm pelo menos **40x40 pixels** de tamanho.

- Verifique se os controles interativos têm pelo menos **5 pixels de espaçamento** entre eles
