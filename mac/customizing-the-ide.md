---
title: Personalizando o IDE
description: O Visual Studio para Mac pode ser personalizado de várias maneiras, permitindo que os usuários desenvolvam aplicativos em um ambiente que atenda tanto suas necessidades estéticas quanto de eficiência. Este artigo explora as diversas maneiras pelas quais Visual Studio para Mac pode ser adaptado para atender às suas necessidades.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2020
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.custom: video
ms.openlocfilehash: 05fd1091a279a085c2a727eb36cbc56fcb201057
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493277"
---
# <a name="customizing-the-ide"></a>Personalizando o IDE

Os Visual Studio para Mac podem ser personalizados, permitindo que os usuários desenvolvam aplicativos em um ambiente que atenda às suas necessidades de eficiência e estética. Este artigo explora as várias formas em que o Visual Studio para Mac pode ser adaptado para atender às suas necessidades.

## <a name="dark-theme"></a>Tema escuro

![Exibição de tema escuro](media/customizing-the-ide-image7a.png)

Você pode alternar os temas em Visual Studio para Mac navegando até o **Visual Studio > preferências > ambiente > estilo visual** e selecionando o tema desejado na lista suspensa **tema da interface do usuário** , conforme ilustrado na imagem a seguir:

![Seleção de tema escuro](media/customizing-the-ide-image7b.png)

## <a name="localization"></a>Localização

O Visual Studio para Mac está traduzido nos 14 idiomas a seguir, permitindo que ele fique acessível para mais desenvolvedores:

* Chinês – China
* Chinês – Taiwan
* Tcheco
* Francês
* Alemão
* Inglês
* Italiano
* Japonês
* Coreano
* Polonês
* Português - Brasil
* Russo
* Espanhol
* Turco

Para alterar o idioma exibido por Visual Studio para Mac, navegue até  **Visual Studio > preferências > ambiente > estilo visual** e selecione o idioma desejado na lista suspensa **idioma da interface do usuário** , conforme ilustrado na imagem a seguir:

![Seleção de Idioma](media/customizing-the-ide-image11a.png)

## <a name="author-information"></a>Informações do autor

O painel de informações do autor permite que você adicione informações relevantes sobre si mesmo como nome, endereço de email, o proprietário dos direitos autorais do seu trabalho, sua empresa e marca registrada:

![Seção Editar Informações do Autor](media/customizing-the-ide-image9a.png)

Essas informações são usadas para popular os cabeçalhos de arquivo padrão, como uma licença, que podem ser adicionadas a novos arquivos:

![Opções de cabeçalho padrão](media/customizing-the-ide-image8a.png)

Os campos **Nome** e **Email** populados serão usados em qualquer confirmação feita por meio do Controle de Versão no Visual Studio para Mac. Se você não tiver preenchido esses campos, Visual Studio para Mac será solicitado a fazê-lo quando você tentar usar o controle de versão.

## <a name="key-bindings"></a>Associações de teclas

Associações de teclas, ou atalhos de teclado, permitem que você adapte seu ambiente de desenvolvimento para que você possa se mover com mais eficiência em Visual Studio para Mac. Ele fornece associações de teclas familiares para muitos IDEs populares, como o Visual Studio (no Windows), o ReSharper, o Visual Studio Code e o Xcode.

Associações de chave podem ser definidas navegando até o **Visual Studio > preferências > ambiente > associações de chave** , conforme ilustrado pela imagem a seguir:

![Definir associações de teclas](media/customizing-the-ide-image10a.png)

Aqui você pode pesquisar combinações de associações de teclas, exibir associações conflitantes, adicionar novas associações e editar as associações existentes.

Essas associações também podem ser definidas durante a configuração inicial do Visual Studio para Mac, por meio da tela de **seleção de teclado** :

![Definir associações de chave, primeira execução](media/ide-tour-2019-keyboard-shortcut.png)

## <a name="workspace-layout"></a>Layout do workspace

O espaço de trabalho de Visual Studio para Mac consiste em uma área de documento principal (normalmente, o editor, a superfície do designer ou o arquivo de opções), rodeado por *janelas de ferramentas* gratuitas que contêm informações úteis para acessar e gerenciar arquivos de aplicativos, testes e depuração.

 ![Layout do workspace](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-tool-windows"></a>Exibindo e organizando janelas de ferramentas

Ao abrir qualquer nova solução ou arquivo em Visual Studio para Mac, você deve observar algumas *janelas de ferramentas* no espaço de trabalho, incluindo a janela da solução, a estrutura de tópicos do documento e os erros:

![Janela de ferramentas](media/customizing-the-ide-image2a.png)

O Visual Studio para Mac fornece janelas de ferramentas que contêm informações adicionais, ferramentas e auxílios de navegação, todas as quais podem ser acessadas navegando no item de menu **Exibir** e selecionando uma janela de ferramentas para adicioná-la:

![Selecionar nova janela de ferramentas](media/customizing-the-ide-image3a.png)

As janelas de ferramentas também podem ser abertas automaticamente por vários comandos, como o comando **Find in Files** (Shift + CMD + F), que abre uma janela desanexada dos resultados da pesquisa.

As janelas de ferramentas podem ser movidas e organizadas em todo o seu fluxo de trabalho de qualquer maneira que seja mais útil para você. Por exemplo, eles podem ser encaixados em qualquer lado do editor de documentos, adjacentes a outra janela de ferramentas, acima ou abaixo de outra janela, ou como um conjunto de janelas com guias, permitindo que você alterne rapidamente entre eles.

Para janelas de ferramentas usadas com frequência, você também pode desanexá-las completamente da janela Visual Studio para Mac e em sua própria janela nova.

As janelas de ferramentas podem ser fixadas e fechadas pelos controles no canto superior direito de cada janela:

:::image type="content" source="media/customizing-the-ide-image5a.png" alt-text="Usando controles para fixar ou fechar janelas de ferramentas":::

As janelas fixas são encaixadas nos lados do espaço de trabalho e permanecem abertas para um acesso mais rápido quando você precisar delas. Janelas desafixadas são encaixadas, mas não são mostradas até que você focalize a guia da janela com um mouse ou foco com o teclado; Eles podem ficar ocultos quando o foco do mouse e do teclado os deixa.

### <a name="organizing-layouts"></a>Organizando layouts

As janelas de ferramentas exibidas a qualquer momento dependem do contexto atual. Por exemplo, ao usar o designer visual, a caixa de ferramentas e as janelas de grade de propriedades são mais importantes; durante a depuração, é útil ter as janelas do depurador para exibir a pilha e os locais.

O estado das janelas de ferramentas abertas é representado por um *layout*. Os layouts podem ser alternados manualmente por meio do menu Exibir, conforme ilustrado na imagem a seguir, ou são alternados automaticamente quando você executa uma ação, como depuração ou abertura de um storyboard:

![Selecionar novos Layouts](media/customizing-the-ide-image6b.png)

É possível criar um novo layout usando a **exibição > layout > salvar o layout atual...** item de menu. Este comando adicionará o layout atual ao menu para que você possa selecioná-lo a qualquer momento:

![Salva o layout atual](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>Suporte à edição lado a lado

O Visual Studio para Mac permite abrir os editores de texto lado a lado ou usar um editor como uma janela flutuante desanexada.

O modo de duas colunas pode ser habilitado por meio do item de menu Exibir selecionando **exibir colunas do editor de > > 2 colunas** ou arrastando uma guia do editor para uma das bordas da área do editor:

![Modo de duas colunas lado a lado](media/customizing-the-ide-sbs.png)

As guias do Editor podem ser arrastadas para fora da área de documento para criar uma janela flutuante do editor. Essa janela flutuante também dá suporte a editores lado a lado e pode conter várias guias do editor:

![Criar nova janela](media/customizing-the-ide-sbs1.png)

![Duas colunas lado a lado com guias adicionais](media/customizing-the-ide-sbs2.png)

Para reverter para um único editor aberto, selecione **Exibir > Colunas do Editor > Uma coluna**.

## <a name="related-video"></a>Vídeo relacionados

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Customize-the-Look-and-Feel/player]

## <a name="see-also"></a>Confira também

- [Personalizar o IDE do Visual Studio (no Windows)](/visualstudio/ide/personalizing-the-visual-studio-ide)