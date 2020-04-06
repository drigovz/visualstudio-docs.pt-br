---
title: Menus e Comandos para Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f22b7ac4377b600208c079b6af1eff7fc3cbfc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698383"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menus e comandos para Visual Studio
## <a name="command-usage"></a>Uso de comando

### <a name="overview"></a>Visão geral
 Ao contrário do Microsoft Office, que é uma suíte que compreende muitos produtos separados, o Visual Studio contém muitos produtos que contribuem com seus comandos para o IDE global do Visual Studio. O IDE gerencia a complexidade de milhares de comandos filtrando a funcionalidade disponível para o usuário com base no contexto.

 Quando o contexto de um usuário muda - como mudar de uma janela de design para uma janela de edição de código - a funcionalidade não relacionada ao novo contexto desaparece. Ao mesmo tempo, novas funcionalidades surgem juntamente com informações dinâmicas relacionadas, como opções Propriedades e Caixa de Ferramentas. O usuário não deve notar a troca do conjunto de comandos disponível. Se o usuário estiver distraído ou confuso com comandos que aparecem ou desaparecem, então o design da ui precisa ser ajustado. O contexto atual do usuário é sempre indicado de uma ou mais maneiras, como na barra de títulos do IDE, na janela Propriedades ou na caixa de diálogo Páginas de propriedade.

 As barras de comando permitem flexibilidade na ui. As únicas estruturas de comando inerentes ao ambiente do Visual Studio são o menu principal e a barra de comando principal, que podem ser personalizadas e até ocultas. Outras barras de comando aparecem e desaparecem com base no estado da aplicação. Janelas de ferramentas e editores de documentos também podem conter barras de ferramentas incorporadas dentro das bordas da janela.

#### <a name="basic-guidelines"></a>Diretrizes básicas

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Use comandos, grupos de comando e menus compartilhados existentes sempre que possível.
 Uma vez que os comandos são normalmente mostrados com base no contexto, o uso de menus compartilhados existentes e grupos de comandos garante que a estrutura de comandos permaneça relativamente estável entre as mudanças de contexto. Reutilizar comandos compartilhados e colocar novos comandos perto de comandos compartilhados relacionados também reduz a complexidade do IDE e cria uma experiência mais fácil de usar. Se um novo comando precisar ser definido, tente colocá-lo em um grupo de comando compartilhado existente. Se um novo grupo precisar ser definido, coloque-o em um menu compartilhado existente perto de um grupo de comando relacionado antes de criar um novo menu de nível superior.

##### <a name="do-not-create-icons-for-every-command"></a>Não crie ícones para cada comando.
 Pense cuidadosamente antes de criar um ícone de comando. Os ícones devem ser criados apenas para comandos que:

- aparecer em uma barra de ferramentas padrão.

- é provável que sejam adicionados pelos usuários a uma barra de ferramentas através da caixa de diálogo **Personalizar...**

- tem um ícone associado à mesma ação em outro produto da Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limitar a adição de atalhos de teclado
 A grande maioria dos usuários emprega uma pequena fração de todos os atalhos disponíveis. Na dúvida, não vincule seu recurso a um atalho de teclado. Trabalhe com sua equipe de experiência do usuário antes de adicionar novos atalhos.

##### <a name="give-commands-a-default-menu-placement"></a>Dê aos comandos uma colocação padrão do menu.
 Esteja ciente de que seus comandos serão personalizados por outros e projete-os de acordo. Não existe um comando oculto. Todos os comandos do Visual Studio aparecem nas **ferramentas > personalizar** a caixa de diálogo, a janela de comando, a conclusão automática, as ferramentas > **opções > diálogo de teclado** e o Ambiente de Ferramentas de Desenvolvimento (DTE). Certifique-se de dar aos seus comandos um nome e uma dica de ferramenta em seu arquivo .ctc para que os usuários possam encontrá-los facilmente.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Não duplicar comandos compartilhados em uma barra de ferramentas incorporada.
 É útil colocar comandos próximos à área de foco do usuário. Uma maneira de fazer isso é criar uma barra de ferramentas incorporada na parte superior da janela da ferramenta ou do editor de documentos. Os comandos colocados na barra de ferramentas devem ser específicos para a região de conteúdo dentro da janela. Não duplicar comandos compartilhados nessas barras de ferramentas. Por exemplo, nunca coloque um ícone "Salvar" em uma barra de ferramentas incorporada.

### <a name="content-and-command-visibility"></a>Visibilidade de conteúdo e comando
 Os comandos existem nos seguintes escopos: **Ambiente,** **Hierarquia**e **Documento.** Conheça cada escopo para ter confiança na colocação de comando.

 Os comandos no escopo **do Ambiente** estabelecem o contexto primário e são compartilhados entre múltiplos contextos. Eles alteram a visibilidade ou arranjo de documentos e janelas de ferramentas. Entre os comandos no escopo do ambiente estão **Novo Projeto,** **Conexão com Servidor,** **Processo de Anexação,** **Corte,** **Cópia,** **Colar,** **Encontrar,** **Opções,** **Personalizar,** **Nova Janela**e Exibir **Ajuda.**

 Os comandos no escopo **Hierarquia** gerenciam hierarquias no Visual Studio, incluindo **Projeto,** **Equipe**e **Dados.** Eles se relacionam com o subcontexto de um projeto - por exemplo, **Debug**, **Build**, **Test,** **Architecture,** or **Analyze**. Entre os comandos no escopo Hierarquia estão **Adicionar novo item,** **nova consulta,** **configurações do projeto,** **adicionar nova fonte de dados,** **assistente de desempenho de lançamento**e **novo diagrama.**

 Os comandos no escopo **Documento** atuam sobre o conteúdo de um documento, como código, design ou uma consulta de item de trabalho (WIQ). Eles também agem na visão de uma janela de ferramenta ou são específicos para essa janela da ferramenta. Os comandos de escopo de documento também atuam nos objetos de arquivo que são específicos da hierarquia, como **Remover do Projeto**. Entre os comandos no escopo do documento estão **Refatorar > Renomear,** **Criar Cópia do Item de Trabalho,** **Expandir Tudo,** **Colapsar Tudo**e Criar Tarefa do **Usuário**.

### <a name="command-placement-decisions"></a>Decisões de posicionamento de comando
 Uma vez que você decidiu criar um comando, você precisará determinar sua colocação apropriada e se criar um atalho de teclado. Siga este caminho de decisão para estabelecer onde colocar o comando:

 ![Gráfico de decisão de colocação de comando](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Caminho de decisão para colocação de comando no Visual Studio**

### <a name="command-placement-in-menus"></a>Colocação de comando em menus

#### <a name="main-menu-bar"></a>Barra de menu principal
 A barra de menu principal deve ser o local padrão para comandos de quaisquer pacotes de menu específicos de contexto que contribuam para a interface do iu. A barra de menu principal difere de outras estruturas de comando, pois o ambiente a usa para controlar quais comandos são visíveis. Todas as outras barras de comando simplesmente desabilitam comandos que estão fora de contexto, sejam eles colocados em um menu ou em uma barra de ferramentas.

 O ambiente define um conjunto de comandos incorporados na barra de menu principal que são comuns em todo o IDE e vários domínios de tarefas. Esses comandos são sempre visíveis, independentemente de quais VSPackages são carregados no ambiente. Embora o VSPackages possa estender este conjunto de comandos, o conjunto de comandos de cada produto e a colocação de seus comandos é responsabilidade de cada equipe.

 A estrutura do menu principal do Visual Studio pode ser dividida nas seguintes categorias de menu:

##### <a name="core-menus"></a>Menus principais

- Arquivo

- Editar

- Exibir

- Ferramentas

- Janela

- Ajuda

##### <a name="project-specific-menus"></a>Menus específicos do projeto

- Project

- Build

- Depurar

##### <a name="context-specific-menus"></a>Menus específicos do contexto

- Equipe

- Dados

- Teste

- Arquitetura

- Analisar

##### <a name="document-specific-menus"></a>Menus específicos de documentos

- Formatar

- Tabela

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Ao projetar menus principais, siga estas regras:

- Não exceda 25 itens de nível superior em um determinado contexto

- Os menus nunca devem exceder 600 pixels de altura.

- Avalie um menu principal em vários contextos, como no SKU Ultimate e no Perfil Geral.

- Menus flyout são aceitáveis.

- Os menus flyout devem conter pelo menos três itens e não mais do que sete.

- Os menus flyout devem ir apenas um nível profundo - alguns itens do menu do Visual Studio têm submenus em cascata, mas esse padrão não é encorajado.

- Não use mais do que seis separadores. Os agrupamentos devem aderir à seguinte ilustração:

     ![Diretrizes para o agrupamento de menus principais](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Embora não seja necessário ter cada agrupamento na figura, a adição de agrupamentos adicionais é restrita.

- Cada agrupamento deve ter de dois a sete itens do menu.

#### <a name="main-menu-ordering"></a>Pedido de menu principal
 Antes de adicionar um novo item de nível superior, considere colocar o comando em um menu de nível superior existente. Ao adicionar um novo menu de nível superior, certifique-se de colocá-lo no local correto. Decida se o menu é específico para projetar, contextualizar ou documentar. Mantenha o nome do menu de nível superior conciso e use apenas uma palavra.

 Os menus principais devem reservar o resto dos comandos. Arquivar, editar e exibir deve estar sempre à esquerda, e Ferramentas, Janela e Ajuda devem estar sempre à direita.

#### <a name="context-menus"></a>Menus de contexto
 Colocar muita funcionalidade dentro dos menus de contexto resulta em uma interface difícil de aprender. Todas as principais funcionalidades devem estar disponíveis através da barra de menu principal. A colocação de comandos deve ser conciliada com os comandos existentes para evitar comandos duplicados. Para menus de contexto, o shell define grupos de menupadrão que devem ser incluídos dependendo se o menu de contexto é para a solução, um nó de projeto ou um item do projeto.

 Ao projetar menus de contexto, siga as mesmas regras do menu principal e, além disso:

- Não exceda 25 itens de menu de nível superior.

- Os menus flyout são aceitáveis, mas não devem exceder um nível profundo - nunca use flyouts em cascata.

- Não use mais do que seis separadores.

### <a name="command-placement-in-toolbars"></a>Posicionamento de comando em barras de ferramentas

#### <a name="general-toolbars"></a>Barras de ferramentas gerais
 Ao projetar e organizar barras de ferramentas, siga estes padrões:

- Não use mais de um verbo por botão. Um botão = uma ação.

- Use o texto ao lado do ícone somente se ele precisar ser reforçado com o rótulo.

- Use uma caixa de combinação exclusivamente para propriedades que serão comutadas várias vezes em uma sessão. Caso contrário, exponha a propriedade em outro lugar.

- A largura de uma caixa combo deve ser igual à largura do item mais longo dentro da caixa + 30%. Por exemplo, se o item mais longo for de 200 pixels, então a caixa de combinação deve ter 260 pixels de largura.

- Limitar o uso de separadores. O uso de um separador ao lado de um dropdown é um anti-padrão, porque a forma do dropdown em si age como um separador visual.

- Os grupos de ícones devem conter de três a seis ícones.

- Se os qualificadores resultarem em vários comandos úteis, use um botão dividido que armazena a última configuração:

     ![Botões divididos no Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Exemplo de um botão dividido. Os seis comandos à esquerda podem, em vez disso, caber em um único botão.**

#### <a name="product-specific-toolbars"></a>Barras de ferramentas específicas do produto
 Cada produto pode fornecer uma barra de ferramentas padrão que contém comandos usados e importantes com freqüência, e a barra de ferramentas padrão de cada produto deve aparecer na primeira vez que o Visual Studio for iniciado após a instalação do produto.

 Os produtos também devem aproveitar grupos de comando compartilhados e menus fornecidos pelo IDE. Cada grupo de comando compartilhado é colocado em um menu compartilhado destinado a organizar comandos relacionados de forma significativa para o usuário. É importante aproveitar essa estrutura de comando compartilhado para reduzir a complexidade.

#### <a name="global-toolbars"></a>Barras de ferramentas globais
 As barras de ferramentas globais são necessárias para caber em uma linha para fora da caixa. Ao criar uma nova barra de ferramentas global, siga as diretrizes para esse tipo de barra de ferramentas.

 **Diretrizes gerais da barra de ferramentas:**

- Cada barra de ferramentas tem 24 pixels em controles comuns (gripper, overflow).

- Cada botão da barra de ferramentas tem 22 pixels de largura, incluindo preenchimento. Fazendo do ícone um botão split adiciona outros 11 pixels de largura.

- A duplicação de comandos em barras de ferramentas é permitida.

  **Barras de ferramentas específicas para documentos** aparecem quando um determinado tipo de arquivo está ativo e desaparece quando um tipo de arquivo diferente se torna ativo.

- As barras de ferramentas específicas para documentos podem não ter mais de 12 botões.

- A largura total da barra de ferramentas não pode exceder 300 pixels.

- Cada tipo de arquivo pode ter uma barra de ferramentas incorporada ou uma barra de ferramentas global específica para documentos, mas não ambas.

  **Barras de ferramentas específicas do contexto** aparecem quando um determinado contexto é definido e tendem a permanecer ativos por longos períodos.

- O limite de botão para todas as barras de ferramentas específicas de contexto é de 18.

- Se a maioria dos usuários não empregar consistentemente os comandos desta barra de ferramentas quando o contexto estiver ativo, então não associe essa barra de ferramentas a um contexto.

- Certifique-se de que a barra de ferramentas desapareça ao sair do contexto. Nenhuma dessas barras de ferramentas deve aparecer na inicialização.

  **Barras de ferramentas sem contexto** nunca aparecem automaticamente. Estes só mostram quando o usuário os ativa. Mantenha a largura máxima abaixo de 200 pixels.

### <a name="general-organization-and-shell-defined-groups"></a>Organização geral e grupos definidos por shell
 Use comandos compartilhados, grupos de comando e menus compartilhados existentes. Se um novo comando precisar ser definido, tente colocá-lo em um grupo de comando compartilhado existente. Se um novo grupo precisar ser definido, tente colocá-lo em um menu compartilhado existente perto de um grupo de comando relacionado antes de criar um novo menu de nível superior. Isso reduz a complexidade do comando e, ao mesmo tempo, garante a colocação consistente de comando no IDE.

 O menu **Formato** compartilhado, normalmente mostrado no contexto das janelas de documentos estilo designer, é ilustrado na imagem a seguir:

 ![Menu Visual Studio Format com chamadas](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Grupos de menus no Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Redução e reutilização de comandos
 Os comandos são normalmente mostrados com base no contexto, a fim de reduzir o número de comandos que o usuário vê a qualquer momento. No entanto, você também deve reutilizar menus compartilhados existentes e grupos de comando para garantir que a estrutura de comando permaneça relativamente estável entre as mudanças de contexto.

 Reutilizar comandos compartilhados e colocar novos comandos perto de comandos compartilhados relacionados reduz a complexidade do IDE e cria uma experiência mais fácil de usar.

## <a name="naming-commands"></a>Comandos de nomeação

### <a name="naming-conventions"></a>Convenções de nomenclatura
 A nomeação consistente de comandos é fundamental para que os usuários possam encontrar e executar comandos, usando a linha de comando ou vinculando-se a um atalho de teclado. Os nomes de comando também ajudam o usuário a entender para que finalidade um comando serve quando é exibido em uma barra de ferramentas ou em um menu em cascata ou contexto.

#### <a name="when-naming-commands"></a>Ao nomear comandos:

- Construa texto para que seja facilmente localizado. Para obter mais informações sobre a localização do texto, consulte [as melhores práticas de localização](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Seja conciso. Os comandos não devem usar mais do que três palavras.

- Use a capitalização do caso do título: a primeira letra de cada palavra deve ser maiúscula. Para obter mais informações sobre a formatação de texto no Visual Studio, consulte [estilo texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Leve em consideração onde o comando será colocado. Está em um menu de alto nível ou um flyout? Por exemplo, ao agrupar comandos de alinhamento em um flyout, o comando de nível superior deve ser "Alinhar" e os comandos de flyout devem ser "Esquerda", "Direita", "Centro", "Justificar" e assim por diante. Seria redundante nomear os comandos de flyout "Alinhar à esquerda" ou "Alinhar à direita".

     ![Menu Visual Studio Format](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Usando ícones com comandos
 Seja poupado no uso do emparelhamento de ícones com comandos. Embora associar uma imagem única a um comando apresse a capacidade do usuário de identificar que o comando, a desordem visual e a ineficiência ocorrem com o uso excessivo da imagem. As seguintes regras ajudam na hora de decidir se criar um ícone de comando.

#### <a name="use-an-icon-with-a-command-only-if"></a>Use um ícone com um comando somente se:

- O mesmo comando tem um ícone associado a ele em outro produto proeminente da Microsoft, como um dos aplicativos do Microsoft Office.

- O comando será colocado em uma barra de ferramentas padrão.

- O comando é um comando especial que os usuários provavelmente adicionarão a uma barra de ferramentas usando a caixa de diálogo **"Personalizar...".**

## <a name="access-and-shortcut-keys"></a>Teclas de acesso e atalho

### <a name="overview"></a>Visão geral
 Existem dois tipos de atribuições chave do teclado:

- **As teclas de acesso** (também conhecidas como aceleradoras) permitem o acesso ao teclado através dos menus para comandar e para cada rótulo na ui de diálogo. As teclas de acesso são principalmente para fins de acessibilidade, são atribuídas a todos os menus e a maioria dos controles da caixa de diálogo, não devem ser memorizadas, afetam apenas a janela atual e são localizadas.

- **As teclas de atalho** usam principalmente seqüências de teclas Control (Ctrl) e Function (Fn). Eles são projetados mais para usuários avançados e ajuda na produtividade. Eles são atribuídos apenas aos comandos mais usados e permitem acesso rápido ao ignorar o menu principal. As teclas de atalho devem ser memorizadas e, por essa razão, devem ser atribuídas de acordo com o esquema de perfil. Os esquemas de teclas de atalho podem variar de perfil para perfil. Um usuário pode personalizar teclas de atalho através de **ferramentas > opções > teclado**.

### <a name="assigning-access-keys"></a>Atribuindo chaves de acesso
 As teclas de acesso consistem em teclas alfanuméricas Alt plus. Atribua uma chave de acesso a cada item do menu sem exceção. Siga o Windows e convenções comuns para atribuir chaves de acesso. por exemplo, a chave de acesso para **Arquivo > Novo** deve ser sempre **Alt, F, N**.

 Não use letras de largura de um pixel, como 'i' (em maiúsculas ou minúsculas) ou um 'l' minúsculo, e evite usar caracteres com descendentes (g, j, p, q e y) pois estes são difíceis de distinguir.

 Evite usar chaves duplicadas quando possível. Nos casos em que a duplicação é inevitável, o sistema de menulida conflitos pedalando através de todos os comandos que usam a chave. Como exemplo, para um hipotético comando "Número" no menu Arquivo que duplica a tecla de acesso "N", **Alt, F, N** criaria um novo arquivo, e **Alt, F, N, N** executaria o comando "Número".

### <a name="assigning-shortcut-keys"></a>Atribuindo teclas de atalho
 Evite atribuir novas teclas de atalho, pois elas não são necessárias para cada comando e tributar o sistema (e a memória do usuário) se forem usados em excesso. Dados do Programa de Melhoria da Experiência do Cliente (CEIP) indicam que os usuários do Visual Studio usam apenas um pequeno subconjunto dos atalhos integrados.

 Ao definir atalhos, siga estas regras:

- **Use seqüências de teclas Control (Ctrl) e Function (Fn).**

- **Preserve atalhos usados com freqüência.** Mantenha os atalhos mais populares.

- **Torne os atalhos do editor fáceis de digitar.** Vincule atalhos fáceis de digitar a comandos que os desenvolvedores mais precisam ao escrever código. Por exemplo, **Edit.InvokeSmartTag** precisa ter uma chave de atalho rápida como Ctrl+/ e não Alt+Shift+F10.

- **Esforce-se por atalhos temáticos consistentemente.**

- **Siga as diretrizes do Windows para determinar quais chaves modificadoras devem ser empregadas.** Use combinações de teclas Ctrl para comandos que tenham efeitos em larga escala, como comandos que se aplicam a um documento inteiro. Use combinações de teclas Shift para comandos que ampliem ou complementem as ações da tecla de atalho padrão. Não use combinações Ctrl+Alt.

- **Remova atalhos estranhos.** Se você tiver um recurso legado, considere remover atalhos que são usados com extrema infreqüência (menos de 10 vezes a partir dos dados CEIP) ou infreqüência moderada (menos de 100 vezes a partir dos dados CEIP) se uma chave de acesso fornecer acesso rápido ao mesmo comando. Por exemplo: Alt, H, C abrirá Ajuda/Conteúdo.

  Não há uma maneira simples de verificar a disponibilidade de atalhos. Se você quiser adicionar um atalho, siga estas etapas:

1. Verifique a lista de atalhos do [Visual Studio 2013](http://visualstudioshortcuts.com/2013/) para determinar se há comandos semelhantes ao grupo seu.

2. Vá para **Ferramentas > Opções > Ambiente > Teclado** e teste seu atalho. Verifique cada esquema de mapeamento do teclado listado em "Aplicar o seguinte esquema adicional de mapeamento do teclado". Verifique os perfis Geral, C#, VB e C++, pois esses compartilham atalhos exclusivos. Seu atalho está disponível se não for mapeado em nenhum desses lugares.
