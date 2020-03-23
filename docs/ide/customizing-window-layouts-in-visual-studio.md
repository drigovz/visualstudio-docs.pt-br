---
title: Personalizar layouts de janela
ms.date: 01/23/2017
ms.topic: conceptual
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1963c76b67eaedea4cdf013739c112275ecffb2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596704"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Personalizar layouts de janela no Visual Studio

No Visual Studio, é possível personalizar a posição, tamanho e comportamento de janelas para criar layouts de janela que funcionam melhor para vários fluxos de trabalho de desenvolvimento. Quando você personaliza o layout, o IDE se lembra dele. Por exemplo, se você alterar o local de encaixe do **Gerenciador de Soluções** e fechar o Visual Studio, na próxima vez que o abrir, mesmo que estiver trabalhando em outro computador, o **Gerenciador de Soluções** estará encaixado no mesmo local.

Também é possível dar um nome ao layout personalizado e salvá-lo e, em seguida, mudar entre layouts com um único comando. Por exemplo, você pode criar um layout para edição e um layout para depuração e alternar entre eles usando o comando **Menu** > **Menu 'Menu'da janela aplicar** janela'

## <a name="kinds-of-windows"></a>Tipos de janelas

### <a name="tool-and-document-windows"></a>Janelas de ferramentas e do documento

O IDE tem dois tipos básicos de janela, *janelas de ferramentas* e *janelas do documento*. As janelas de ferramentas incluem **Solution Explorer,** **Server Explorer,** **Output Window**, **Error List,** os designers, as janelas de depurador e assim por diante. As janelas do documento contêm arquivos de código-fonte, arquivos de texto arbitrário, arquivos de configuração e assim por diante. As janelas de ferramentas podem ser redimensionadas e arrastadas por sua barra de título. Janelas de documento podem ser arrastadas por sua guia. Clique com o botão direito do mouse na guia ou na barra de título para definir outras opções na janela.

O menu **Janela** mostra opções para encaixar, flutuar e ocultar janelas no IDE. Clique com o botão direito do mouse na guia de janela ou na barra de título para ver outras opções para essa janela específica. É possível exibir mais de uma instância de determinadas janelas de ferramentas por vez. Por exemplo, é possível exibir mais de uma janela do navegador da Web e é possível criar outras instâncias de algumas janelas de ferramentas escolhendo **Nova Janela** no menu **Janela**.

### <a name="preview-tab-document-windows"></a>Guia Visualização (janelas do documento)

Na guia **Visualização,** você pode visualizar arquivos no editor sem abri-los. Você pode visualizar arquivos escolhendo-os no **Solution Explorer,** durante a depuração quando você entrar em arquivos, com **Go to Definition,** e quando você navegar através de resultados de uma pesquisa. Os arquivos de visualização são exibidos em uma guia à direita da caixa de guias de documentos. O arquivo será aberto para edição se você modificá-lo ou escolher **Abrir**.

### <a name="tab-groups"></a>Grupos de guias

Os grupos de guias ampliam sua capacidade de gerenciar o workspace limitado ao trabalhar com dois ou mais documentos abertos no IDE. É possível organizar várias janelas do documento e de ferramentas em grupos de guias verticais ou horizontais e embaralhar os documentos de um grupo de guias em outro.

### <a name="split-windows"></a>Dividir janelas

Quando é necessário exibir ou editar dois locais ao mesmo tempo em um documento, é possível dividir as janelas. Para dividir seu documento em duas seções de rolagem independente, clique em **Dividir** no menu **Janela**. Clique em **Remover Divisão** no menu **Janela** para restaurar o modo de exibição único.

### <a name="toolbars"></a>Barras de Ferramentas

As barras de ferramentas podem ser organizadas arrastando ou usando a caixa de diálogo **Personalizar**. Para obter mais informações sobre como posicionar e personalizar barras de ferramentas, consulte [Como: Personalizar menus e barras de ferramentas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Organizar e encaixar janelas

Uma janela do documento e uma janela de ferramentas podem ser *encaixadas* para que tenham uma posição e um tamanho dentro do quadro de janela do IDE ou flutuando como uma janela separada independente do IDE. As janelas de ferramentas podem ser encaixadas em qualquer lugar dentro do quadro do IDE; algumas janelas de ferramentas podem ser encaixadas como janelas com guias no quadro do editor. As janelas do documento podem ser encaixadas dentro do quadro do editor e podem ser fixadas em sua posição atual na ordem de tabulação. Você pode acoplar várias janelas para flutuar juntos em uma *balsa* sobre ou fora do IDE. As janelas de ferramentas também podem ser ocultadas ou minimizadas.

É possível organizar janelas das seguintes maneiras:

- Fixe as janelas do documento à esquerda da caixa de guias.

- Encaixe janelas de guias no quadro de edição.

- Encaixe janelas de ferramentas na borda de um quadro no IDE.

- Faça janelas do documento ou de ferramentas flutuar no IDE ou fora dele.

- Oculte as janelas de ferramentas ao longo da borda do IDE.

- Exiba janelas em monitores diferentes.

- Redefina o posicionamento da janela para o layout padrão ou para um layout personalizado salvo.

Organize as janelas de ferramentas e do documento arrastando-as, usando comandos no menu **Janela** ou clicando com o botão direito do mouse na barra de título da janela a ser organizada.

### <a name="dock-windows"></a>Encaixar janelas

Quando você clica e arrasta a barra de título de uma janela de ferramentas ou a guia da janela do documento, um losango do guia é exibido. Durante a operação de arrastar, quando o cursor do mouse está sobre uma das setas no losango, será exibida uma área sombreada que mostra onde a janela será encaixada se você soltar o botão do mouse no momento.

Para mover uma janela encaixável sem ajustá-la no local, pressione a tecla **Ctrl** enquanto você arrasta a janela.

Para devolver uma janela de ferramenta ou janela de documento ao seu local de encaixe mais recente, pressione **Ctrl** enquanto você clica duas vezes na barra de título ou na guia da janela.

A ilustração a seguir mostra o losango do guia para janelas de documentos, que só podem ser encaixadas dentro do quadro de edição:

![Losango do guia da janela do documento](../ide/media/documentwindowguidediamonds.png)

As janelas de ferramentas podem ser fixadas em um lado de um quadro no IDE ou dentro do quadro de edição. Um guia do losango será exibido quando você arrastar uma janela de ferramentas para outro lugar para ajudá-lo a reencaixar a janela facilmente.

![Losangos do guia da janela de ferramentas](../ide/media/vs10guidediamond.png)

A ilustração a seguir mostra o **Gerenciador de Soluções** que está sendo encaixado em um novo local que é delimitado pela área sombreada azul:

![Encaixando o Gerenciador de Soluções em uma nova posição](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Fechar e ocultar automaticamente janelas de ferramentas

Você pode fechar uma janela de ferramentas clicando no **X** no canto superior direito da barra de título. Para reabrir a janela, use o respectivo atalho de teclado ou comando de menu. As janelas de ferramenta suportam um recurso chamado *auto hide*, o que faz com que uma janela deslize para fora do caminho quando você usa uma janela diferente. Quando uma janela é ocultada automaticamente, o nome dela é exibido em uma guia na borda do IDE. Para usar a janela novamente, aponte para a guia para que a janela volte a ser exibida.

![Ocultar automaticamente](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Para definir se o ocultação automático opera nas janelas da ferramenta individualmente ou como grupos **ancorados,** selecionar ou limpar o botão Auto Hide afeta janelas ativas de ferramentas apenas na caixa de diálogo **Opções.** Para obter mais informações, consulte [Geral, Ambiente, Caixa de diálogo Opções](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> As janelas de ferramentas que têm ocultar automaticamente habilitado poderão ser exibidas temporariamente quando a janela estiver em foco. Para ocultar a janela novamente, selecione um item fora da janela atual. Quando a janela perde o foco, ela não é mais exibida.

### <a name="specifying-a-second-monitor"></a>Especificando um segundo monitor

Se você tiver um segundo monitor e seu sistema operacional der suporte a ele, será possível escolher qual monitor exibirá uma janela. Você pode até agrupar várias janelas em *balsas* em outros monitores.

> [!TIP]
> É possível criar várias instâncias do **Gerenciador de Soluções** e movê-las para outro monitor. Clique com o botão direito do mouse na janela e escolha **Novo Modo de Exibição do Gerenciador de Soluções**. Você pode retornar todas as janelas de volta ao monitor original clicando duas vezes enquanto escolhe a tecla **Ctrl.**

### <a name="reset-name-and-switch-between-window-layouts"></a>Redefinir, nomear e mudar entre layouts de janela

É possível voltar o IDE para o layout de janela original para sua coleção de configurações usando o comando **Redefinir Layout de Janela**. Quando você executar esse comando, as seguintes ações ocorrerão:

- Todas as janelas serão movidas para as posições padrão.

- As janelas fechadas no layout de janela padrão serão fechadas.

- As janelas abertas no layout de janela padrão serão abertas.

### <a name="create-and-save-custom-layouts"></a>Criar e salvar layouts personalizados

O Visual Studio permite salvar até 10 layouts de janela personalizados e mudar rapidamente entre eles. As etapas a seguir mostram como criar, salvar, invocar e gerenciar layouts personalizados que usam vários monitores com janelas de ferramentas encaixadas e flutuantes.

Primeiro, crie uma solução de teste que tem dois projetos, cada um com um layout ideal diferente.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Criar um projeto de interface do usuário e personalizar o layout

1. Crie um projeto de **Aplicativo do WPF** do C#. Imagine que, neste projeto, você vai estar desenvolvendo uma interface do usuário. Você deseja maximizar o espaço da janela de designer e tirar outras janelas de ferramentas do caminho.

2. Se você tiver vários monitores, leve a janela **Gerenciador de Soluções** e o janela **Propriedades** sobre o segundo monitor. Em um sistema de monitor único, tente fechar todas as janelas exceto o designer.

3. Pressione **Ctrl**+**Alt**+**X** para exibir a janela da caixa **de ferramentas.** Se a janela estiver encaixada, arraste-a para que ela flutue em algum lugar que você gostaria de posicioná-la.

4. Pressione **F5** para colocar o Visual Studio em modo de depuração. Ajuste a posição das janelas de **depuração autos,** **pilha de chamadas**e **saída** do jeito que você deseja. O layout que você está prestes a criar será aplicado ao modo de edição e ao modo de depuração.

5. Quando seus layouts no modo de depuração e no modo de edição forem como você deseja, escolha **'Esquema de salvamento de janelas'** da **janela** > . Chame esse layout de "Designer".

     Observe que seu novo layout é atribuído ao próximo atalho de teclado da lista reservada de **Ctrl**+**Alt**+**1...0**.

#### <a name="create-a-database-project-and-layout"></a>Criar um layout e um projeto de banco de dados

1. Adicione um novo projeto de **Banco de Dados do SQL Server** à solução.

2. Clique com o botão direito do mouse sobre o novo projeto no **Solution Explorer** e escolha Exibir no **Object Explorer**. Isso exibe a janela **Gerenciador de Objetos do SQL Server**, que permite acessar tabelas, modos de exibição e outros objetos em seu banco de dados. É possível fazer essa janela flutuar ou deixá-la encaixada. Ajuste as outras janelas de ferramentas da maneira como você as desejar. Para obter maior realismo, é possível adicionar um banco de dados real, mas isso não é necessário para esse passo a passo.

3. Quando o layout é como você deseja, no menu principal escolha **'Janela** > **Salvar janela' Layout**da janela . Chame esse layout de “Projeto de Banco de Dados”. (Não nos preocuparemos com um layout de modo de depuração para este projeto.)

#### <a name="switch-between-the-layouts"></a>Mudar entre os layouts

Para alternar entre layouts, use os atalhos do teclado ou no menu principal, escolha **'Janela** > **Aplicar esquema 'Janela'.**

![Aplicar menu de layout de janela](../ide/media/vs2015_applywindowlayout.png)

Depois de aplicar o layout da interface do usuário, observe como ele é preservado tanto no modo de edição quanto no modo de depuração.

Se você tiver vários monitores no trabalho e um laptop de um só monitor em casa, será possível criar layouts otimizados para cada computador.

> [!NOTE]
> Se você aplicar um layout de vários monitor em um sistema de monitor único, as janelas flutuantes inseridas no segundo monitor ficarão ocultas agora atrás da janela do Visual Studio. Você pode trazer essas janelas para a frente pressionando **Alt + Tab**. Se você abrir o Visual Studio mais tarde com vários monitores, você pode restaurar as janelas para suas posições especificadas reaplicando o layout.

#### <a name="manage-and-roam-your-layouts"></a>Gerenciar e usar perfil móvel nos seus layouts

Você pode remover, renomear ou reordenar seu layout personalizado **escolhendo** > **Layouts de janela de gerenciamento de janelas**. Se você mover um layout, a associação de teclas será ajustada automaticamente para refletir a nova posição na lista. Do contrário, as associações não poderão ser modificadas e, assim, será possível armazenar, no máximo, 10 layouts por vez.

![Gerenciar layouts de janelas](../ide/media/managewindowlayouts.png)

Para lembrar a si mesmo qual atalho de teclado é atribuído a qual layout, escolha **'Janela** > **Aplicar esquema 'Janela'.**

Esses layouts usam perfis móveis automaticamente entre edições do Visual Studio e também entre instâncias do Blend em computadores separados e de qualquer edição Express para qualquer outra organização Express. No entanto, os layouts não usam perfis móveis entre o Visual Studio, o Blend e o Express.

## <a name="see-also"></a>Confira também

- [Como: Mover-se no IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)
