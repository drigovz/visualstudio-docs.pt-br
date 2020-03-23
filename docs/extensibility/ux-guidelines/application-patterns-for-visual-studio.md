---
title: Padrões de aplicação para o Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55044df3898b452e87ec877f9ae10dd12a2b1110
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303186"
---
# <a name="application-patterns-for-visual-studio"></a>Padrões de aplicativo para Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Interações de janela

### <a name="overview"></a>Visão geral
Os dois principais tipos de janelas usados no Visual Studio são editores de documentos e janelas de ferramentas. Raros, mas possíveis, são grandes diálogos de modelagem. Embora sejam todas modeless na concha, seus padrões são fundamentalmente diferentes. Esta seção cobre a diferença entre janelas de documentos, janelas de ferramentas e diálogos de modelagem. Os padrões de diálogo modal são abordados em [Diálogos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Comparando padrões de uso de janelas
**As janelas de** documento são quase sempre exibidas dentro do documento. Isso dá ao editor de documentos um "estágio central" para organizar janelas de ferramentas suplementares ao redor.

Uma **janela de ferramenta** é mais frequentemente exibida como uma janela separada e menor desabou contra a borda do IDE. Isso pode ser visível, escondido ou auto-escondido. No entanto, às vezes as janelas de ferramentas são apresentadas dentro do documento bem, desverificando a propriedade **Janela/Docking** na janela. Isso resulta em mais imóveis, mas também uma decisão de design comum: ao tentar se integrar ao Visual Studio, você deve decidir se seu recurso deve exibir uma janela de ferramenta ou uma janela de documento.

**Diálogos de modelagem** são desencorajados no Visual Studio. A maioria dos diálogos modeless são, por definição, janelas de ferramentas flutuantes e devem ser implementadas dessa forma. Diálogos de modelagem são permitidos nos casos em que o tamanho de uma janela de ferramenta normal encaixada ao lado da concha seria muito limitador. Eles também são permitidos nos casos em que o usuário provavelmente moveria o diálogo para um monitor secundário.

Pense cuidadosamente sobre qual tipo de recipiente você precisa. Considerações comuns do padrão de uso para o design de IU estão na tabela a seguir.

||Janela do documento|Janela da ferramenta|Diálogo de modelagem|
|-|---------------------|-----------------|---------------------|
| **Posição** | Sempre posicionado dentro do documento bem e não encaixa nas bordas do IDE. Ele pode ser "puxado" para que ele flutue separadamente da concha principal. | Geralmente, encaixe as guias ao redor das bordas do IDE, mas pode ser personalizado para ser flutuante, auto-escondido (não fixado) ou ancorado dentro do documento bem.|Grande janela flutuante separada do IDE. |
| **Modelo de compromisso** | *Compromisso atrasado*<br /><br /> Para salvar os dados em um documento, o usuário deve emitir o comando **Salvar o &gt; arquivo,** **salvar as**ou **salvar todos.** Uma janela de documento tem o conceito dos dados dentro dele sendo "sujos" e depois comprometidos com um dos comandos de salvamento. Ao fechar uma janela de documento, todo o conteúdo é salvo em disco ou perdido. | *Compromisso imediato*<br /><br /> Não há modelo de salvamento. Para janelas de ferramentas de inspetor que auxiliam na edição de um arquivo, o arquivo deve ser aberto no editor ativo ou designer, e o editor ou designer possui o save. | *Compromisso atrasado ou imediato*<br /><br /> Na maioria das vezes, um diálogo de grande modelagem requer uma ação para cometer alterações e permite uma operação "Cancelar", que reverte quaisquer alterações feitas dentro da sessão de diálogo.  Isso diferencia uma caixa de diálogo modeless de uma janela de ferramenta em que as janelas da ferramenta sempre têm um modelo de confirmação imediata. |
| **Visibilidade** | *Abrir/criar (arquivo) e Fechar*<br /><br /> A abertura de janelas de documentos é feita através da abertura de um documento existente ou do uso de um modelo para criar um novo documento. Não há comando \<"Abra> de editor específico". | *Esconder e mostrar*<br /><br /> As janelas de ferramentas de instância única podem ser ocultadas ou mostradas. Os conteúdos e estados dentro da janela da ferramenta persistem, seja à vista ou escondidos. Janelas de ferramentas de várias instâncias podem ser fechadas, bem como ocultas. Quando uma janela de ferramenta de várias instâncias é fechada, o conteúdo e o estado dentro da janela da ferramenta são descartados. | *Lançado a partir de um comando*<br /><br /> Os diálogos são iniciados a partir de um comando baseado em tarefas. |
| **Instâncias** | *Multiinstância*<br /><br /> Vários editores podem ser abertos ao mesmo tempo e editando arquivos diferentes, enquanto alguns editores também permitem que o mesmo arquivo seja aberto em mais de um editor (usando o comando **Janela &gt; Nova Janela).**<br /><br /> Um único editor pode estar editando um ou vários arquivos ao mesmo tempo (Project Designer). | *Uma ou várias instâncias*<br /><br /> O conteúdo muda para refletir o contexto (como no Navegador de Propriedades) ou empurrar o foco/contexto para outras janelas (Lista de tarefas, Explorador de Soluções).<br /><br /> As janelas de ferramentas de instância única e de várias instâncias devem ser associadas à janela ativa do documento, a menos que haja uma razão convincente para não fazê-lo. | *Instância única* |
| **Exemplos** | **Editores de**texto, como o editor de código<br /><br /> **Superfícies de**design, como um designer de formulários ou uma superfície de modelagem<br /><br /> **Layouts de controle semelhantes aos diálogos,** como o Manifest Designer | O **Solution Explorer** fornece uma solução e projetos contidos dentro da solução<br /><br /> O **Server Explorer** fornece uma visão hierárquica dos servidores e conexões de dados que o usuário escolhe abrir na janela. Abrir um objeto da hierarquia do banco de dados, como uma consulta, abre uma janela de documento e permite que o usuário edite a consulta.<br /><br /> O **Navegador de Propriedades** exibe propriedades para o objeto selecionado em uma janela de documento ou em outra janela de ferramenta. As propriedades são apresentadas em uma exibição de grade hierárquica ou em controles complexos semelhantes a diálogos e permitem que o usuário defina os valores para essas propriedades. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Janelas de ferramentas

### <a name="overview"></a>Visão geral
As janelas de ferramentas suportam o trabalho do usuário que acontece nas janelas de documentos. Eles podem ser usados para exibir uma hierarquia que representa um objeto raiz fundamental que o Visual Studio fornece e pode manipular.

Ao considerar uma nova janela de ferramentas no IDE, os autores devem:

- Use janelas de ferramentas existentes apropriadas para tarefas e não crie novas com funcionalidade semelhante. Novas janelas de ferramentas só devem ser criadas se oferecerem uma "ferramenta" ou funcionalidade significativamente diferente que não pode ser integrada em uma janela semelhante, ou transformando uma janela existente em um hub de pivotação.

- Use uma barra de comando padrão, se necessário, na parte superior da janela da ferramenta.

- Seja consistente com padrões já presentes em outras janelas de ferramentas para apresentação de controle e navegação do teclado.

- Seja consistente com a apresentação de controle em outras janelas de ferramentas.

- Tornar o windows de ferramenta específico de documento visível automaticamente quando possível, de modo que eles apareçam somente quando o documento pai estiver ativado.

- Certifique-se de que o conteúdo da janela é navegável pelo teclado (teclas de seta de suporte).

#### <a name="tool-window-states"></a>Estados da janela da ferramenta
As janelas de ferramentas do Visual Studio têm estados diferentes, alguns dos quais são ativados pelo usuário (como o recurso de ocultação automática). Outros estados, como o autovisível, permitem que janelas de ferramentas apareçam no contexto correto e se escondam quando não for necessário. Há cinco estados de janela de ferramentas no total.

- As janelas de ferramentas **encaixadas/fixadas** podem ser anexadas a qualquer um dos quatro lados da área do documento. O ícone pushpin aparece na barra de título da janela da ferramenta. A janela da ferramenta pode ser encaixada horizontal ou verticalmente ao longo da borda da concha e outras janelas da ferramenta, e também pode ser ligada a guias.

- As janelas de ferramentas **auto-ocultas** não são fixadas. A janela pode deslizar para fora da vista, deixando uma guia (com o nome da janela da ferramenta e seu ícone) na borda da área do documento. A janela da ferramenta desliza para fora quando um usuário paira sobre a guia.

- As janelas de ferramentas **auto-visíveis** aparecem automaticamente quando outra peça de ida e volta, como um editor, é lançada ou ganha foco.

- Janelas de ferramentas **flutuantes** pairam fora do IDE. Isso é útil para configurações de vários monitores.

- As janelas da ferramenta **de documento com guias** podem ser encaixadas dentro do documento. Isso é útil para grandes janelas de ferramentas, como o Object Browser, que precisam de mais imóveis do que a copamento às bordas do quadro permite.

![Estados da janela da ferramenta no Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Estados da janela da ferramenta no Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Instância única e multiinstância
As janelas de ferramentas são de instância única ou de várias instâncias. Algumas janelas de ferramentas de instância única podem estar associadas à janela ativa do documento, enquanto janelas de ferramentas de várias instâncias podem não ser. As janelas de ferramentas de várias instâncias respondem ao comando **Janela &gt; Nova Janela** criando uma nova instância da janela. A imagem a seguir ilustra uma janela de ferramenta que habilita o comando Nova janela quando uma instância da janela estiver ativa:

![Janela da ferramenta habilitando o comando 'Nova janela' quando uma instância da janela está ativa](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Janela da ferramenta habilitando o comando 'Nova janela' quando uma instância da janela está ativa

As janelas de ferramentas de instância única podem ser ocultadas ou mostradas, enquanto janelas de ferramentas de várias instâncias podem ser fechadas, bem como ocultas. Todas as janelas da ferramenta podem ser encaixadas, vinculadas a guias, flutuantes ou definidas como uma janela de criança De Interface de Vários Documentos (MDI) (semelhante a uma janela de documento). Todas as janelas de ferramenta devem responder aos comandos apropriados de gerenciamento de janelas no menu Janela:

![Comandos de gerenciamento de janelas no menu Visual Studio Window](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Comandos de gerenciamento de janelas no menu Visual Studio Window

#### <a name="document-specific-tool-windows"></a>Janelas de ferramentas específicas para documentos
Algumas janelas de ferramentas são projetadas para mudar com base em um determinado tipo de documento. Essas janelas são atualizadas continuamente para refletir a funcionalidade aplicável à janela de documento ativa no IDE.

Exemplos de janelas de ferramentas cujo conteúdo altera para refletir o editor selecionado são a Caixa de Ferramentas e o Contorno de Documentos. Essas janelas mostram uma marca d'água quando um editor tem foco que não oferece contexto à janela.

#### <a name="navigable-list-tool-windows"></a>Janelas de ferramentas de lista navegável
Algumas janelas de ferramentas exibem uma lista de itens navegáveis com os quais o usuário pode interagir. Neste tipo de janela, deve haver sempre feedback para o item atual da lista, mesmo que a janela esteja inativa. A lista deve responder aos comandos **GoToNextLocation** e **GoToPrevLocation** alterando também o item selecionado na janela

Exemplos de janelas de ferramentas de lista navegáveis são o Solution Explorer e a janela Find Results.

### <a name="tool-window-types"></a>Tipos de janelas de ferramentas

#### <a name="common-tool-windows-and-their-functions"></a>Janelas de ferramentas comuns e suas funções

**Janelas de ferramentas hierárquicas**

| Janela da ferramenta | Função |
| --- | --- |
| Gerenciador de Soluções | Uma árvore hierárquica que exibe uma lista de documentos contidos em projetos, arquivos diversos e itens de solução. A exibição dos itens dentro dos projetos é definida pelo pacote que possui o tipo de projeto (por exemplo, tipos baseados em referência, baseados em diretório ou de modo misto). |
| Exibição de Classe | Uma árvore hierárquica das classes e vários elementos no conjunto de trabalho dos documentos, independente dos próprios arquivos. |
| Gerenciador de Servidores | Uma árvore hierárquica que exibe todos os servidores e conexões de dados na solução. |
| Estrutura de Tópicos do Documento | A estrutura hierárquica do documento ativo. |

**Janelas de ferramentas de grade**

| Janela da ferramenta | Função |
| --- | --- |
| Propriedades | Uma grade que exibe uma lista de propriedades para o objeto selecionado, juntamente com os catadores de valor para editar essas propriedades. |
| Lista de Tarefas | Uma grade que permite ao usuário criar/editar/excluir tarefas e comentários. |

**Janelas de ferramentas de conteúdo**

| Janela da ferramenta | Função |
| --- | --- |
| Ajuda | Uma janela que permite aos usuários acesso a vários métodos de obter ajuda, a partir de "Como faço?" vídeos para fóruns MSDN. |
| Ajuda dinâmica | Uma janela de ferramenta que exibe links para ajudar tópicos aplicáveis à seleção atual. |
| Pesquisador de Objetos | Um conjunto de quadros de duas colunas com uma lista de componentes hierárquicos de objeto no painel esquerdo e as propriedades e métodos do objeto na coluna direita. |

**Janelas de ferramentas de diálogo**

| Janela da ferramenta | Função |
| --- | --- |
| Localizar | Uma caixa de diálogo que permite ao usuário encontrar ou encontrar e substituir em vários arquivos dentro da solução. |
| Localização Avançada | Uma caixa de diálogo que permite ao usuário encontrar ou encontrar e substituir em vários arquivos dentro da solução. |

**Outras janelas de ferramentas**

::: moniker range="vs-2017"

| Janela da ferramenta | Função |
| --- | --- |
| Caixa de Ferramentas | A janela da ferramenta usada para armazenar elementos que serão jogados em superfícies de design, fornecendo uma fonte de arrasto consistente para todos os designers. |
| Start Page | Portal do usuário para o Visual Studio, com acesso a feeds de notícias de desenvolvedores, ajuda visual studio e projetos recentes. Os usuários também podem criar páginas iniciais personalizadas copiando o arquivo StartPage.xaml do diretório de arquivos do programa "Common7\IDE\StartPages\" Visual Studio para a pasta StartPages no diretório de documentos do Visual Studio e, em seguida, editando o XAML à mão ou abrindo-o no Visual Studio ou outro editor de código. |

::: moniker-end

::: moniker range=">=vs-2019"

| Janela da ferramenta | Função |
| --- | --- |
| Caixa de Ferramentas | A janela da ferramenta usada para armazenar elementos que serão jogados em superfícies de design, fornecendo uma fonte de arrasto consistente para todos os designers. |

::: moniker-end

**Janelas de ferramentas de depurador**

| Janela da ferramenta | Função |
| --- | --- |
| Autos ||
| Imediata ||
| Saída | A janela de saída pode ser usada sempre que você tiver eventos texulos ou status para declarar. |
| Memória ||
| Pontos de interrupção ||
| Executando ||
| Documentos ||
| Pilha de chamadas ||
| Locais ||
| Relógios ||
| Desmontagem ||
| Registros ||
| Threads ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Convenções de editores de documentos

### <a name="document-interactions"></a>Interações documentais
O "documento bem" é o maior espaço dentro do IDE e é onde o usuário geralmente tem focado sua atenção para completar suas tarefas, auxiliado por janelas de ferramentas suplementares. Os editores de documentos representam as unidades fundamentais de trabalho que o usuário abre e salva dentro do Visual Studio. Eles mantêm um forte senso de seleção vinculado ao Solution Explorer ou outras janelas de hierarquia ativa. O usuário deve ser capaz de apontar para uma dessas janelas de hierarquia e saber onde o documento está contido e sua relação com a solução, o projeto ou outro objeto raiz fornecido por um pacote do Visual Studio.

A edição de documentos requer uma experiência de usuário consistente. Para permitir que o usuário se concentre na tarefa em questão, em vez de no gerenciamento de janelas e na localização de comandos, selecione uma estratégia de exibição de documento que melhor se encaixe nas tarefas do usuário para editar esse tipo de documento.

#### <a name="common-interactions-for-the-document-well"></a>Interações comuns para o documento bem

- Mantenha um modelo de interação consistente nas experiências **comuns de Arquivo Novo** e **Arquivo Aberto.**

- Atualize a funcionalidade relacionada em janelas e menus relacionados quando a janela do documento for aberta.

- Os comandos do menu são adequadamente integrados em menus comuns como **Editar,** **Formato**e **Exibir** menus. Se uma quantidade substancial de comandos especializados estiver disponível, então um novo menu pode ser criado. Este novo menu só deve ser visível quando o documento tiver foco.

- Uma barra de ferramentas incorporada pode ser colocada na parte superior do editor. Isso é preferível ter uma barra de ferramentas separada que aparece fora do editor.

- Mantenha sempre uma seleção no Solution Explorer ou na janela de hierarquia ativa semelhante.

- Clicar duas vezes em um documento no Solution Explorer deve executar a mesma ação **que Abrir**.

- Se mais de um editor puder ser usado em um tipo de documento, o usuário poderá substituir ou redefinir a ação padrão em um determinado tipo de documento usando a caixa de diálogo **Abrir com** o botão direito do mouse no arquivo e selecionando **Abrir com** no menu de atalho.

- Não construa um assistente em um documento bem.

### <a name="user-expectations-for-specific-document-types"></a>Expectativas dos usuários para tipos de documentos específicos
Existem vários tipos básicos diferentes de editores de documentos e cada um tem um conjunto de interações que são consistentes com outros do mesmo tipo.

- **Editor baseado em texto:** editor de código, arquivos de log

- **Superfície de design:** WPF forma designer, formulários do Windows

- **Editor de estilo de diálogo:** Manifest Designer, propriedades do projeto

- **Designer de modelos:** designer de fluxo de trabalho, codemap, diagrama de arquitetura, progressão

Existem também vários tipos de não-editores que usam bem o documento. Embora eles não editem documentos sozinhos, eles precisam seguir interações padrão para janelas de documentos.

- **Relatórios:** Relatório IntelliTrace, relatório Hyper-V, relatório profiler

- **Painel:** Hub de Diagnósticos

#### <a name="text-based-editors"></a>Editores baseados em texto

- O documento participa do modelo de guia de visualização, permitindo a visualização do documento sem abri-lo.

- A estrutura do documento pode ser representada dentro de uma janela de ferramenta complementar, como um esboço de documento.

- O IntelliSense (se for o caso) se comportará consistentemente com outros editores de código.

- Pop-ups ou iU assistiva seguem estilos e padrões semelhantes para a ui semelhante existente, como codelens.

- As mensagens relativas ao status do documento serão apresentadas em um controle de infobar na parte superior do documento ou na barra de status.

- O usuário deve ser capaz de personalizar a aparência de fontes e cores usando uma página **De Opções de > de Ferramentas,** seja a página Fontes e Cores compartilhadas ou uma específica para o editor.

#### <a name="design-surfaces"></a>Superfícies de design

- Um designer vazio deve ter uma marca d'água na superfície indicando como começar.

- Os mecanismos de comutação de visualização seguirão padrões existentes, como clicar duas vezes para abrir um editor de código ou guias dentro da janela do documento, permitindo interação com ambos os painéis.

- A adição de elementos à superfície de design deve ser feita através da Caixa de Ferramentas, a menos que seja necessária uma janela de ferramenta altamente específica.

- Os itens na superfície seguirão um modelo de seleção consistente.

- As barras de ferramentas incorporadas contêm apenas comandos específicos de documentos, e não comandos comuns, como **Save**.

#### <a name="dialog-style-editors"></a>Editores estilo diálogo

- O layout de controle deve seguir as convenções normais de layout de diálogo.

- As guias dentro do editor não devem coincidir com a aparência das guias do documento, elas devem corresponder a um dos dois estilos de guia de interior permitidos.

- Os usuários devem ser capazes de interagir com os controles usando apenas teclado; ativando o editor e passando por controles ou usando mnemônicos padrão.

- O designer deve usar o modelo Save comum. Nenhum botão geral Salvar ou cometer deve ser colocado na superfície, embora outros botões possam ser apropriados.

#### <a name="model-designers"></a>Designers de modelos

- Um designer vazio deve ter uma marca d'água na superfície indicando como começar.

- A adição de elementos à superfície de design deve ser feita através da Caixa de Ferramentas.

- Os itens na superfície seguirão um modelo de seleção consistente.

- As barras de ferramentas incorporadas contêm apenas comandos específicos de documentos, e não comandos comuns, como **Save**.

- Uma lenda pode aparecer na superfície, seja indicativa ou uma marca d'água.

- O usuário deve ser capaz de personalizar a aparência das fontes/cores usando uma página **De Opções de > de Ferramentas,** seja na página Fontes e Cores compartilhadas ou uma específica para o editor.

#### <a name="reports"></a>Relatórios

- Os relatórios são normalmente somente informações e não participam do modelo Salvar. No entanto, eles podem incluir interação, como links para outras informações relevantes ou seções que se expandem e colapsam.

- A maioria dos comandos na superfície deve ser hiperlinks, não botões.

- O layout deve incluir um cabeçalho e seguir as diretrizes padrão do layout do relatório.

#### <a name="dashboards"></a>Painéis

- Os dashboards não têm um modelo de interação em si, mas servem como um meio de oferecer uma variedade de outras ferramentas.

- Eles não participam do modelo Save.

- Os usuários devem ser capazes de interagir com os controles usando apenas o teclado, seja ativando o editor e guiando através de controles ou usando mnemônicos padrão.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>Diálogos

### <a name="introduction"></a>Introdução
Os diálogos no Visual Studio devem normalmente suportar uma unidade discreta do trabalho do usuário e, em seguida, ser demitidos.

Se você determinou que precisa de um diálogo, você tem três opções, por ordem de preferência:

1. Integre seus recursos em um dos diálogos compartilhados no Visual Studio.

2. Crie sua própria caixa de diálogo usando um padrão encontrado em uma caixa de diálogo semelhante existente.

3. Crie um novo diálogo, seguindo as diretrizes de interação e layout.

Esta seção descreve como escolher o padrão de diálogo correto nos fluxos de trabalho do Visual Studio e as convenções comuns para o design de diálogo.

### <a name="themes"></a>Temas
Os diálogos no Visual Studio seguem um dos dois estilos básicos:

#### <a name="standard-unthemed"></a>Padrão (sem tema)
A maioria dos diálogos são diálogos de utilidade padrão e devem ser destemáticos. Não remodele os controles comuns ou tente criar botões ou controles "modernos" estilizados. Controles e aparência cromada seguem [as diretrizes padrão de interação do Windows Desktop para caixas de diálogo](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>Temáticos
Diálogos especiais de "assinatura" podem ser temáticos. Diálogos temáticos têm uma aparência distinta, que também tem alguns padrões especiais de interação associados ao estilo. Tema sua caixa de diálogo somente se atender a esses requisitos:

- O diálogo é uma experiência comum que será vista e usada com frequência ou por muitos usuários (por exemplo, o **diálogo Novo Projeto.**

- A caixa de diálogo contém elementos proeminentes da marca do produto (por exemplo, a **caixa de diálogo Configurações da** conta).

- O diálogo aparece como parte integrante de um fluxo maior que inclui outros diálogos temáticos (por exemplo, o **diálogo Adicionar serviço conectado).**

- O diálogo é uma parte importante de uma experiência que desempenha um papel estratégico na promoção ou diferenciação de uma versão do produto.

Ao criar um diálogo temático, use as cores do ambiente apropriadas e siga os padrões corretos de layout e interação. (Veja [layout para visual studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Projeto de diálogo
Diálogos bem desenhados levam em consideração os seguintes elementos:

- A tarefa do usuário que está sendo suportada

- O estilo de texto de diálogo, linguagem e terminologia

- Escolha de controle e convenções de IU

- Especificação do layout visual e alinhamento de controle

- Acesso pelo teclado

#### <a name="content-organization"></a>Organização de conteúdo
Considere as diferenças entre esses tipos básicos de diálogos:

- [Diálogos simples](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) apresentam controles em uma única janela modal. A apresentação pode incluir variações de padrões de controle complexos, incluindo um seletor de campo ou uma barra de ícones.

- [Diálogos em camadas](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) são usados para aproveitar ao máximo os imóveis de tela quando uma única peça de ida e volta compreende vários grupos de controles. Os agrupamentos da caixa de diálogo são "em camadas" através de controles de guia, controles de lista de navegação ou botões para que o usuário possa escolher qual agrupamento ver a qualquer momento.

- [Os assistentes](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) são úteis para direcionar o usuário através de uma seqüência lógica de passos para a conclusão de uma tarefa. Uma série de opções são oferecidas em painéis sequenciais, às vezes introduzindo diferentes fluxos de trabalho ("ramos") dependendo de uma escolha feita no painel anterior.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Diálogos simples
Um diálogo simples é uma apresentação de controles em uma única janela modal. Esta apresentação pode incluir variações de padrões de controle complexos, como um catador de campo. Para diálogos simples, siga o layout geral padrão, bem como qualquer layout específico necessário para agrupamentos de controle complexos.

![>Criar Chave nome forte é um exemplo de um diálogo simples no Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Create Strong Name Key é um exemplo de um diálogo simples no Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Diálogos em camadas
As caixas de diálogo em camadas incluem guias, painéis e árvores incorporadas. Eles são usados para maximizar imóveis quando há vários grupos de controles oferecidos em um único pedaço de ui. Os agrupamentos são em camadas para que o usuário possa escolher qual agrupamento ver a qualquer momento.

No caso mais simples, o mecanismo para alternar entre agrupamentos é um controle de guia. Existem várias alternativas disponíveis. Consulte Priorizando e colocando em camadas como escolher o estilo mais adequado.

A caixa de diálogo **Opções de &gt; ** ferramentas é um exemplo de uma caixa de diálogo em camadas usando uma árvore incorporada:

![Ferramentas > Options é um exemplo de uma caixa de diálogo em camadas no Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Ferramentas > Options é um exemplo de uma caixa de diálogo em camadas no Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>Assistentes
Os assistentes são úteis para direcionar o usuário através de uma seqüência lógica de etapas na conclusão de uma tarefa. Uma série de opções são oferecidas em painéis sequenciais, e o usuário deve continuar em cada etapa antes de prosseguir para o próximo. Uma vez que existam padrões suficientes, o botão **Concluir** está ativado.

 Os magos modais são usados para tarefas que:

- Contenha ramificações, onde diferentes caminhos são oferecidos dependendo das escolhas do usuário

- Contêm dependências entre etapas, onde as etapas subseqüentes dependem da entrada do usuário das etapas anteriores

- São suficientemente complexos que a UI deve ser usada para explicar as escolhas oferecidas e os possíveis resultados em cada etapa

- São transacionais, exigindo um conjunto de etapas a serem concluídas em sua totalidade antes que quaisquer alterações sejam cometidas

### <a name="common-conventions"></a>Convenções comuns
Para obter o design e a funcionalidade ideais com seus diálogos, siga essas convenções sobre tamanho do diálogo, posição, padrões, configuração e alinhamento de controle, texto de UI, barras de título, botões de controle e teclas de acesso.

Para obter diretrizes específicas do layout, consulte [Layout para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Tamanho
Os diálogos devem caber dentro de uma resolução de tela mínima de 1024x768, e o tamanho inicial da caixa de diálogo não deve exceder 900x700 pixels. Diálogos podem ser resizáveis, mas não é um requisito.

Existem duas recomendações para diálogos resizáveis:

1. Que um tamanho mínimo é definido para o diálogo que otimizará para o conjunto de controle sem recorte, e ajustar-se para acomodar um crescimento razoável de localização.

2. Que o tamanho escalado pelo usuário persiste de sessão em sessão. Por exemplo, se o usuário dimensionar uma caixa de diálogo para 150%, então um lançamento subsequente da caixa de diálogo será exibido em 150%.

#### <a name="position"></a>Posição
Os diálogos devem aparecer centrados no IDE no primeiro lançamento. A última posição de diálogos não resizáveis não precisa ser persistida, de modo que eles aparecerão centrados em lançamentos subseqüentes.

Para diálogos resizáveis, o tamanho deve ser persistido em lançamentos subseqüentes. Para diálogos modais reizáveis, a posição não precisa ser persistiu. Exibi-los centrados no IDE impede que a caixa de diálogo apareça em uma posição imprevisível ou inutilizável quando a configuração de exibição do usuário foi alterada.

Para diálogos de modelagem que possam ser reposicionados, a posição do usuário deve ser mantida em lançamentos subseqüentes, pois a caixa de diálogo pode ser usada frequentemente como parte integrante de um fluxo de trabalho maior.

Quando os diálogos devem gerar outros diálogos, o diálogo mais alto deve ser em cascata para a direita e para baixo do pai, de modo que seja óbvio para o usuário que ele navegou para um novo lugar.

#### <a name="modality"></a>Modalidade
Ser modal significa que os usuários são obrigados a completar ou cancelar a caixa de diálogo antes de continuar. Uma vez que os diálogos modais bloqueiam a interação do usuário com outras partes do ambiente, o fluxo de tarefas do seu recurso deve usá-los o mais moderadamente possível. Quando uma operação modal é necessária, o Visual Studio tem uma série de diálogos compartilhados em que você pode integrar seus recursos. Se você deve criar um novo diálogo, siga o padrão de interação de uma caixa de diálogo existente com funcionalidade semelhante.

Quando os usuários precisam realizar duas atividades ao mesmo tempo, como **Encontrar** e **Substituir** enquanto escrevem um novo código, a caixa de diálogo deve ser modelada para que o usuário possa facilmente alternar entre eles. O Visual Studio geralmente usa janelas de ferramentas para esse tipo de tarefa vinculada ao editor.

#### <a name="control-configuration"></a>Configuração de controle
Seja consistente com as configurações de controle existentes que realizam a mesma coisa no Visual Studio.

#### <a name="title-bars"></a>Barras de título

- O texto na barra de títulodeve refletir o nome do comando que o lançou.

- Nenhum ícone deve ser usado nas barras de título de diálogo. Nos casos em que o sistema requer um, use o logotipo do Visual Studio.

- Os diálogos não devem ter minimizado ou maximizado os botões.

- Os botões de ajuda na barra de título foram preteridos. Não os adicione a novos diálogos. Quando eles existem, eles devem lançar um tópico de Ajuda que seja conceitualmente relevante para a tarefa.

  ![Especificações de diretrizes para barras de título em diálogos visual studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Especificações de diretrizes para barras de título em diálogos visual studio

#### <a name="control-buttons"></a>Botões de controle
Em geral, os botões **OK**, **Cancel**e **Ajuda** devem ser dispostos horizontalmente no canto inferior direito da caixa de diálogo. A pilha vertical alternativa é permitida se uma caixa de diálogo tiver vários outros botões na parte inferior da caixa de diálogo que apresentariam confusão visual com os botões de controle.

![Configurações aceitáveis para botões de controle em diálogos do Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Configurações aceitáveis para botões de controle em diálogos do Visual Studio

A caixa de diálogo deve incluir um botão de controle padrão. Para determinar o melhor comando a ser usado como padrão, escolha entre as seguintes opções (listadas por ordem de precedência):

- Escolha o comando mais seguro e seguro como padrão. Isso significa escolher o comando mais provável para evitar a perda de dados e evitar o acesso não intencional do sistema.

- Se a perda de dados e a segurança não forem fatores, escolha o comando padrão com base na conveniência. Incluindo o comando mais provável, o padrão melhorará o fluxo de trabalho do usuário quando a caixa de diálogo suportar tarefas frequentes ou repetitivas.

Evite escolher uma ação permanentemente destrutiva para o comando padrão. Se tal comando estiver presente, escolha um comando mais seguro como padrão.

#### <a name="access-keys"></a>Chaves de acesso
Não use teclas de acesso para botões **OK,** **Cancel**ou **Help.** Esses botões são mapeados para teclas de atalho por padrão:

| Nome do botão | Atalho do teclado |
| --- | --- |
| OK | Digite |
| Cancelar | Esc |
| Ajuda | F1 |

#### <a name="imagery"></a>Imagens
Use imagens com moderação nos diálogos. Não use ícones grandes em diálogos apenas para usar o espaço. Use imagens somente se elas forem uma parte importante da transmissão da mensagem para o usuário, como ícones de aviso ou animações de status.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Priorizando e colocando camadas

#### <a name="prioritizing-your-ui"></a>Priorizando sua ida e futura
Pode ser necessário trazer certos elementos de IU para a vanguarda e colocar comportamentos e opções mais avançadas (incluindo comandos obscuros) em diálogos. Traga a funcionalidade comumente usada para a vanguarda, abrindo espaço para ela, e tornando-a visível por padrão na ui com um rótulo de texto quando a caixa de diálogo é mostrada.

#### <a name="layering-your-ui"></a>Camadas da sua ui
Se você determinou que um diálogo é necessário, mas a funcionalidade relacionada que você deseja apresentar ao usuário vai além do que pode ser exibido em um diálogo simples, então você precisa colocar a sua interface de usuário em camadas. Os métodos de camadamais comuns que o Visual Studio usa são abas e corredores ou dashboards. Em alguns casos, regiões que podem se expandir e entrar em colapso podem ser apropriadas. A iu adaptativa geralmente não é recomendada no Visual Studio.

Existem vantagens e desvantagens para diferentes métodos de iu de camadas através de controles semelhantes a guias. Revise a lista abaixo para garantir que você está escolhendo uma técnica de camadas adequada à sua situação.

##### <a name="tabbing"></a>Tabulação

| Mecanismo de comutação | Vantagens e uso adequado | Desvantagens e uso inadequado |
| --- | --- | --- |
| Controle guia | Logicamente agrupar páginas de diálogo em conjuntos relacionados<br /><br />Útil para menos de cinco (ou o número de guias que se encaixam em uma linha através da caixa de diálogo) páginas de controles relacionados na caixa de diálogo<br /><br />Os rótulos das guias devem ser curtos: uma ou duas palavras que podem identificar facilmente o conteúdo<br /><br />Um estilo de diálogo de sistema comum<br /><br />Exemplo: **Propriedades &gt; do item do explorador de arquivos** | Fazer rótulos curtos descritivos pode ser difícil<br /><br />Geralmente não escala mais de cinco guias em uma caixa de diálogo<br /><br />Inapropriado se você tiver muitas abas para uma linha (use uma técnica alternativa de camadas)<br /><br />Não é extensível |
| Navegação de barra lateral | Dispositivo de comutação simples que pode acomodar mais categorias do que guias<br /><br />Lista plana de categorias (sem hierarquia)<br /><br />Extensível<br /><br />Exemplo: **Personalizar... Adicionar &gt; comando** | Não é um bom uso do espaço horizontal se houver menos de três grupos<br /><br />Tarefa pode ser mais adequada para um drop-down |
| Controle de árvore | Permite categorias ilimitadas<br /><br />Permite agrupamento e/ou hierarquia de categorias<br /><br />Extensível<br /><br />Exemplo: ** &gt; Opções de ferramentas** | Hierarquias fortemente aninhadas podem causar rolagem horizontal excessiva<br /><br />Visual Studio tem uma abundância de visualizações de árvores |
| Assistente | Ajuda na conclusão da tarefa orientando o usuário através de etapas seqüenciais baseadas em tarefas: o assistente representa uma tarefa de alto nível e os painéis individuais representam subtarefas necessárias para realizar a tarefa geral<br /><br />Útil quando a tarefa cruza os limites da UI, como quando o usuário teria que usar vários editores e janelas de ferramentas para completar a tarefa<br /><br />Útil quando a tarefa requer ramificação<br /><br />Útil quando a tarefa contém dependências entre etapas<br /><br />Útil quando várias tarefas semelhantes com um garfo de decisão podem ser apresentadas em um diálogo para reduzir o número de diferentes diálogos semelhantes | Inapropriado para qualquer tarefa que não exija um fluxo de trabalho seqüencial<br /><br />Os usuários podem ficar sobrecarregados e confusos por um assistente com muitos passos<br /><br />Os assistentes têm imóveis de tela inerentemente limitados |

##### <a name="hallways-or-dashboards"></a>Corredores ou painéis
Corredores e painéis são diálogos ou painéis que servem como pontos de lançamento para outros diálogos e janelas. O "corredor" bem projetado imediatamente supera apenas as opções, comandos e configurações mais comuns, permitindo que o usuário realize prontamente tarefas comuns. Como um corredor do mundo real fornece portas para acessar os quartos atrás deles, aqui a ui menos comum é coletada em "quartos" separados (muitas vezes outros diálogos) de funcionalidades relacionadas que podem ser acessadas a partir do corredor principal.

Alternativamente, uma iu que oferece todas as funcionalidades disponíveis em uma única coleção em vez de refatorar a funcionalidade menos comum em locais separados é simplesmente um painel de instrumentos.

![Conceito de corredor para expor ui adicional no Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Conceito de corredor para expor ui adicional no Outlook

##### <a name="adaptive-ui"></a>Interface do usuário adaptável
Mostrar ou ocultar a ui com base no uso ou na experiência autorreferida de um usuário é outra maneira de apresentar a iu necessária enquanto oculta outras partes. Isso não é recomendado no Visual Studio, pois os algoritmos para decidir quando mostrar ou esconder a ui pode ser complicado, e as regras sempre estarão erradas para alguns casos.

## <a name="projects"></a><a name="BKMK_Projects"></a>Projetos

### <a name="projects-in-the-solution-explorer"></a>Projetos no Explorador de Soluções
A maioria dos projetos são classificados como baseados em referência, baseados em diretórios ou mistos. Todos os três tipos de projetos são suportados simultaneamente no Solution Explorer. A raiz da experiência do usuário em trabalhar com projetos ocorre dentro desta janela. Embora diferentes nós de projeto sejam projetos de referência, diretório ou tipo de modo misto, há um padrão de interação comum que deve ser aplicado como ponto de partida antes de divergir em padrões de usuário específicos do projeto.

Os projetos devem sempre:

- Apoie a capacidade de adicionar pastas de projeto para organizar conteúdos de projetos

- Manter um modelo consistente para persistência do projeto

Os projetos também devem manter modelos de interação consistentes para:

- Remoção de itens do projeto

- Salvando documentos

- Edição de propriedades do projeto

- Editando o projeto em uma visão alternativa

- Operações de arrastar e soltar

### <a name="drag-and-drop-interaction-model"></a>Modelo de interação de arrastar e soltar
Os projetos tipicamente se classificam como baseados em referência (capazes de persistir apenas referências a itens de projeto no armazenamento), baseados em diretórios (capazes de persistir apenas itens de projeto fisicamente armazenados dentro da hierarquia de um projeto) ou misturados (capazes de persistir referências ou itens físicos). O IDE acomoda todos os três tipos de projetos simultaneamente dentro do **Solution Explorer**.

De uma perspectiva de arrastar e soltar, as seguintes características devem ser aplicadas a cada tipo de projeto dentro do **Solution Explorer**:

- **Projeto baseado em referência:** O ponto chave é que o projeto está arrastando uma referência a um item no armazenamento. Quando um projeto baseado em referência atua como fonte de uma operação de movimento, ele só deve remover a referência ao item do projeto. O item não deve ser realmente excluído do disco rígido. Quando um projeto baseado em referência age como um alvo para uma operação de movimento (ou cópia), ele deve adicionar uma referência ao item de origem original sem fazer uma cópia privada do item.

- **Projeto baseado em diretório:** Do ponto de vista drag-and-drop, o projeto está arrastando em torno do item físico em vez de uma referência. Quando um projeto baseado em diretório age como uma fonte para uma operação de movimento, ele deve acabar excluindo o item físico do disco rígido, bem como removendo-o do projeto. Quando um projeto baseado em diretório age como um alvo para uma operação de movimentação (ou cópia), ele deve fazer uma cópia do item de origem em seu local de destino.

- **Projeto de alvo misto:** Do ponto de vista de arrastar e soltar, o comportamento desse tipo de projeto baseia-se na natureza do item que está sendo arrastado (seja uma referência a um item no armazenamento ou ao próprio item). O comportamento correto para referências e itens físicos são descritos acima.

Se houvesse apenas um tipo de projeto no **Solution Explorer,** então as operações de arrastar e soltar seriam simples. Como cada sistema de projeto tem a capacidade de definir seu próprio comportamento de arrastar e soltar, certas diretrizes (baseadas no comportamento de arrastar e soltar do Windows Explorer) devem ser seguidas para garantir uma experiência previsível do usuário:

- Uma operação de arrasto não modificada no **Solution Explorer** (quando nem as teclas Ctrl nem Shift são mantidas para baixo) deve resultar em uma operação de movimento.

- A operação de arrasto de turno também deve resultar em uma operação de movimento.

- A operação ctrl-drag deve resultar em uma operação de cópia.

- Os sistemas de projeto baseados em referência e mistos suportam a noção de adicionar um link (ou referência) ao item de origem. Quando esses projetos são alvo de uma operação de arrastar e soltar (quando **ctrl + shift** é retido), deve resultar em uma referência ao item a ser adicionado ao projeto

Nem todas as operações de arrastar e soltar são sensatas em combinações de projetos mistos baseados em referência, baseados em diretórios e com base em referências. Em particular, é problemático fingir permitir uma operação de movimentação entre um projeto de origem baseado em diretório e um projeto de destino baseado em referência, porque o projeto baseado em diretório de origem terá que excluir o item de origem após a conclusão da mudança. O projeto baseado em referência de destino acabaria então com uma referência a um item excluído.

Também é enganoso fingir permitir uma operação de cópia entre esses tipos de projetos porque o projeto baseado em referência de destino não deve fazer uma cópia independente do item de origem. Da mesma forma, ctrl + shift arrastando para um projeto-alvo baseado em diretório não deve ser permitido porque um projeto baseado em diretório é incapaz de persistir referências. Nos casos em que a operação arrastar e soltar não for suportada, o IDE deve proibir a queda e mostrar ao usuário o cursor sem queda (mostrado na tabela de ponteiros abaixo).

Para implementar adequadamente o comportamento de arrastar e soltar, o projeto de origem do arrasto precisa comunicar sua natureza ao projeto-alvo. (Por exemplo, é baseado em referência ou diretório?) Essas informações são indicadas pelo formato da área de transferência que é oferecido pela fonte. Como fonte de uma operação de arrastar (ou cópia `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` de prancheta) um projeto deve oferecer ou respectivamente, dependendo se o projeto é baseado em referência ou baseado em diretório. Ambos os formatos têm o mesmo conteúdo de `CF_HDROP` dados, que é semelhante ao formato do Windows,`NULL` exceto que `Projref` as listas de `IVsSolution::GetProjrefOfItem` strings, em vez de serem nomes de arquivos, são uma lista de strings com término duplo (conforme retornado ou `::GetProjrefOfProject` conforme apropriado).

Como alvo de uma operação de queda (ou pasta `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS`de prancheta), um projeto deve aceitar ambos e, embora o manuseio exato da operação de arrastar e soltar varie dependendo da natureza do projeto de destino e do projeto de origem. O projeto de origem declara sua `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS`natureza por oferecer ou . O alvo da queda entende sua própria natureza e, portanto, tem informações suficientes para tomar decisões sobre se um movimento, cópia ou link deve ser realizado. O usuário também modifica qual operação de arrastar e soltar deve ser realizada pressionando as teclas Ctrl, Shift ou Ctrl e Shift. É importante que o alvo de queda indique `DragEnter` adequadamente `DragOver` qual operação será realizada com antecedência em seus métodos e métodos. O **Solution Explorer** sabe automaticamente se o projeto de origem e o projeto de destino são o mesmo projeto.

Arrastar itens de projeto através de instâncias do Visual Studio (por exemplo, de uma instância de devenv.exe para outra) não é especificamente suportado. O **Solution Explorer** também desativa isso diretamente.

O usuário deve sempre ser capaz de determinar o efeito de uma operação de arrastar e soltar selecionando um item, arrastando-o para o local de destino e observando qual dos seguintes ponteiros do mouse aparece antes que o item seja descartado:

| Ponteiro do mouse | Comando | Descrição |
| :---: | --- | --- |
| ![Ícone mouse "sem queda"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Sem queda | O item não pode ser descartado para o local especificado. |
| ![Ícone de "copiar" do mouse](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Cópia | O item será copiado para o local de destino. |
| ![Ícone de "mover" do mouse](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Mover | O item será movido para o local de destino. |
| ![Ícone de "adicionar referência" do mouse](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Adicionar referência | Uma referência ao item selecionado será adicionada ao local de destino. |

#### <a name="reference-based-projects"></a>Projetos baseados em referência
 A tabela a seguir resume as operações de arrastar e soltar (bem como cortar/copiar/colar) que devem ser executadas com base na natureza do item de origem e das teclas modificadoras pressionadas para projetos-alvo baseados em referência:

| Modificador | Categoria | Item de origem: Referência/Link | Item fonte: Item físico`CF_HDROP`ou sistema de arquivos ( ) |
| --- | --- | --- | --- |
| Sem modificador | Ação | Mover | Link |
| Sem modificador | Destino | Adiciona referência ao item original | Adiciona referência ao item original |
| Sem modificador | Fonte | Exclui referência ao item original | Retém o item original |
| Sem modificador | Result | `DROPEFFECT_MOVE`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | `DROPEFFECT_LINK`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento |
| Shift+Drag | Ação | Mover | Sem queda |
| Shift+Drag | Destino | Adiciona referência ao item original | Sem queda |
| Shift+Drag | Fonte | Exclui referência ao item original | Sem queda |
| Shift+Drag | Result | `DROPEFFECT_MOVE`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | Sem queda |
| Ctrl+Drag | Ação | Cópia | Sem queda |
| Ctrl+Drag | Destino | Adiciona referência ao item original | Sem queda |
| Ctrl+Drag | Fonte | Retém referência ao item original | Sem queda |
| Ctrl+Drag | Result | `DROPEFFECT_COPY`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | Sem queda |
| Ctrl+Shift+Drag | Ação | Link | Link |
| Ctrl+Shift+Drag | Destino | Adiciona referência ao item original | Adiciona referência ao item original |
| Ctrl+Shift+Drag | Fonte | Retém referência ao item original | Retém o item original |
| Ctrl+Shift+Drag | Result | `DROPEFFECT_LINK`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | `DROPEFFECT_LINK`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento |
| Ctrl+Shift+Drag | Observação | O mesmo que o comportamento de arrastar e soltar para atalhos no Windows Explorer. ||
| Corte/colar | Ação | Mover | Link |
| Corte/colar | Destino | Adiciona referência ao item original | Adiciona referência ao item original |
| Corte/colar | Fonte | Retém referência ao item original|Retém o item original |
| Corte/colar | Result | Item permanece em localização original no armazenamento | Item permanece em localização original no armazenamento |
| Copiar/Colar | Ação | Cópia | Link |
| Copiar/Colar | Fonte | Adiciona referência ao item original | Adiciona referência ao item original |
| Copiar/Colar | Result | Retém referência ao item original | Retém o item original |
| Copiar/Colar | Ação | Item permanece em localização original no armazenamento | Item permanece em localização original no armazenamento |

#### <a name="directory-based-projects"></a>Projetos baseados em diretórios
A tabela a seguir resume as operações de arrastar e soltar (bem como cortar/copiar/colar) que devem ser executadas com base na natureza do item de origem e das teclas modificadoras pressionadas para projetos-alvo baseados em diretórios:

| Modificador | Categoria | Item de origem: Referência/Link | Item fonte: Item físico`CF_HDROP`ou sistema de arquivos ( ) |
|-----------------|----------| - | - |
| Sem modificador | Ação | Mover | Mover |
| Sem modificador | Destino | Copia o item para o local de destino | Copia o item para o local de destino |
| Sem modificador | Fonte | Exclui referência ao item original | Exclui referência ao item original |
| Shift+Drag | Ação | Mover | Mover |
| Shift+Drag | Destino | Copia o item para o local de destino | Copia o item para o local de destino |
| Shift+Drag | Fonte | Exclui referência ao item original | Exclui item do local original |
| Shift+Drag | Result | `DROPEFFECT_MOVE`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | `DROPEFFECT_MOVE`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento |
| Ctrl+Drag | Ação | Cópia | Cópia |
| Ctrl+Drag | Destino | Copia o item para o local de destino | Copia o item para o local de destino |
| Ctrl+Drag | Fonte | Retém referência ao item original | Retém referência ao item original |
| Ctrl+Drag | Result | `DROPEFFECT_COPY`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | `DROPEFFECT_COPY`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento |
| Ctrl+Shift+Drag | | Sem queda | Sem queda |
| Corte/colar | Ação | Mover | Mover |
| Corte/colar | Destino | Copia o item para o local de destino | Copia o item para o local de destino |
| Corte/colar | Fonte | Exclui referência ao item original | Exclui item do local original |
| Corte/colar | Result | Item permanece em localização original no armazenamento | Item é excluído do local original no armazenamento |
| Copiar/Colar | Ação | Cópia | Cópia |
| Copiar/Colar | Destino | Adiciona referência ao item original | Copia o item para o local de destino |
| Copiar/Colar | Fonte | Retém o item original | Retém o item original |
| Copiar/Colar | Result | Item permanece em localização original no armazenamento | Item permanece no armazenamento ins localização original |

#### <a name="mixed-target-projects"></a>Projetos de meta-alvo misto
A tabela a seguir resume as operações de arrastar e soltar (bem como cortar/copiar/colar) que devem ser executadas com base na natureza do item de origem e das teclas modificadoras pressionadas para projetos de destino misto:

| Modificador | Categoria | Item de origem: Referência/Link | Item fonte: Item físico`CF_HDROP`ou sistema de arquivos ( ) |
| --- | --- | --- | --- |
| Sem modificador | Ação | Mover | Mover |
| Sem modificador | Destino | Adiciona referência ao item original | Copia o item para o local de destino |
| Sem modificador | Fonte | Exclui referência ao item original | Exclui referência ao item original |
| Sem modificador | Result | `DROPEFFECT_ MOVE`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | `DROPEFFECT_ MOVE`é devolvido como `::Drop` ação e item é excluído do local original no armazenamento |
| Shift+Drag | Ação | Mover | Mover |
| Shift+Drag | Destino | Adiciona referência ao item original | Copia o item para o local de destino |
| Shift+Drag | Fonte | Exclui referência ao item original | Exclui item do local original |
| Shift+Drag | Result | `DROPEFFECT_ MOVE`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | `DROPEFFECT_ MOVE`é devolvido como `::Drop` ação e item é excluído do local original no armazenamento |
| Ctrl+Drag | Ação | Cópia | Cópia |
| Ctrl+Drag | Destino | Adiciona referência ao item original | Copia o item para o local de destino |
| Ctrl+Drag | Fonte | Retém referência ao item original | Retém o item original |
| Ctrl+Drag | Result | `DROPEFFECT_ COPY`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | `DROPEFFECT_ COPY`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento |
| Ctrl+Shift+Drag | Ação | Link | Link |
| Ctrl+Shift+Drag | Destino | Adiciona referência ao item original | Adiciona referência ao item de origem original |
| Ctrl+Shift+Drag | Fonte | Retém referência ao item original | Retém o item original |
| Ctrl+Shift+Drag | Result | `DROPEFFECT_ LINK`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento | `DROPEFFECT_ LINK`é devolvido como `::Drop` ação e item permanece em localização original no armazenamento |
| Corte/colar | Ação | Mover | Mover |
| Corte/colar | Destino | Copia o item para o local de destino | Copia o item para o local de destino |
| Corte/colar | Fonte | Exclui referência ao item original | Exclui item do local original |
| Corte/colar | Result | Item permanece em localização original no armazenamento | Item é excluído do local original no armazenamento |
| Copiar/Colar | Ação | Cópia | Cópia |
| Copiar/Colar | Destino | Adiciona referência ao item original | Copia o item para o local de destino |
| Copiar/Colar | Fonte | Retém o item original | Retém o item original |
| Copiar/Colar | Result | Item permanece em localização original no armazenamento | Item permanece em localização original no armazenamento |

Esses detalhes devem ser levados em consideração ao implementar o arrasto no **Solution Explorer**:

- Design para vários cenários de seleção.

- Os nomes dos arquivos (caminho completo) devem ser únicos em todo o projeto de destino ou a queda não deve ser permitida.

- Os nomes das pastas devem ser únicos (insensíveis a casos) no nível em que estão sendo descartados.

- Existem diferenças de comportamento entre arquivos que estão abertos ou fechados no momento do arrasto (não mencionados em cenários acima).

- Arquivos de nível superior se comportam ligeiramente diferente dos arquivos em pastas.

Outra questão a ser atenta é como lidar com operações de movimentação em itens que possuem designers ou editores abertos. O comportamento esperado é o seguinte (isso se aplica a todos os tipos de projetos):

1. Se o editor/designer aberto não tiver nenhuma alteração não salva, a janela editor/designer deve ser fechada silenciosamente.

2. Se o editor/designer aberto tiver alterações não salvas, então a fonte do arrasto deve esperar que a queda ocorra e, em seguida, peça ao usuário para salvar as alterações não comprometidas nos documentos abertos antes de fechar a janela com um prompt semelhante ao seguinte:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Isso dá ao usuário a oportunidade de salvar o trabalho em andamento antes que o alvo faça suas cópias. Um novo `IVsHierarchyDropDataSource2::OnBeforeDropNotify` método foi adicionado para permitir esse manuseio.

Em seguida, o destino copiará o estado do item como está no armazenamento (sem incluir as alterações não salvas no editor se o usuário escolher **Não**). Após a meta ter concluído `IVsHierarchyDropDataSource::Drop`sua cópia (in), a fonte tem a oportunidade `IVsHierarchyDropDataSource::OnDropNotify`de completar a parte de exclusão da operação de movimento (in ).

Todos os editores com alterações não salvas devem ser deixados abertos. Para aqueles documentos com alterações não salvas, isso significa que a parte de cópia da operação de movimentação será realizada, mas a parte de exclusão será abortada. Em um cenário de seleção múltipla quando o usuário escolhe **Não,** esses documentos com alterações não salvas não devem ser fechados ou removidos, mas aqueles sem alterações não salvas devem ser fechados e removidos.