---
title: Definir as fontes e o tema de cores
ms.date: 11/20/2017
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eccbc834f4038ec18c2f84244488b81a59ecbfbf
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531567"
---
# <a name="personalize-the-visual-studio-ide-and-editor"></a>Personalizar o Editor e o IDE do Visual Studio

Neste tutorial, que leva de 5 a 10 minutos, personalizaremos o tema de cores do Visual Studio, selecionando o tema escuro. Além disso, personalizaremos as cores para dois tipos diferentes de texto no editor de texto.

::: moniker range="vs-2017"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para instalá-lo gratuitamente.

::: moniker-end

## <a name="set-the-color-theme"></a>Definir o tema de cores

O tema de cores padrão da interface do usuário do Visual Studio é chamado **Azul**. Vamos alterar para **Escuro**.

1. Na barra de menus, que é a linha de menus, como **Arquivo** e **Editar**, escolha **Ferramentas** > **Opções**.

1. Na página de opções **Ambiente** > **Geral**, altere a seleção **Tema de cores** para **Escuro** e, em seguida, escolha **OK**.

   O tema de cores para todo o IDE (ambiente de desenvolvimento) do Visual Studio é alterado para **Escuro**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 no tema escuro](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 no tema escuro](media/vs-2019/dark-theme.png)

   ::: moniker-end

> [!TIP]
> É possível instalar temas predefinidos adicionais baixando e instalando o **Visual Studio Color Theme Editor** do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Depois que você instalar essa ferramenta, temas de cores adicionais serão exibidos na lista suspensa **Tema de cores**.

## <a name="change-text-color"></a>Alterar a cor do texto

Agora, personalizaremos algumas cores de texto do editor. Primeiro, vamos criar um arquivo XML para ver as cores padrão.

1. Na barra de menus, escolha **Arquivo** > **Novo** > **Arquivo**.

1. Na caixa de diálogo **Novo Arquivo**, na categoria **Geral**, escolha **Arquivo XML** e escolha **Abrir**.

1. Cole o seguinte XML abaixo da linha que contém o `<?xml version="1.0" encoding="utf-8"?>`.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Observe que os números de linha são azul-turquesa e os atributos XML (como `id="bk101"`) são azul-claro. Vamos alterar a cor do texto desses itens.

   ![Cores de fonte do arquivo XML](media/quickstart-personalize-xml-file.png)

1. Para abrir a caixa de diálogo **Opções**, escolha **Ferramentas** > **Opções** na barra de menus.

1. Em **Ambiente**, escolha a categoria **Fontes e Cores**.

   Observe que o texto em **Mostrar configurações para** diz **Editor de Texto**&mdash; e é isto o que queremos. Expanda a lista suspensa apenas para ver a lista abrangente dos locais em que você pode personalizar as fontes e a cor do texto.

1. Para alterar a cor do texto de números de linha, a lista **Exibir itens**, escolha **Número de Linha**. Na caixa **Primeiro plano do item**, escolha **Verde-oliva**.

   ![Caixa de diálogo Opções, categoria Fontes e Cores](media/quickstart-personalize-line-number-color.png)

   Algumas linguagens têm suas próprias configurações específicas de fontes e cores. Se você for um desenvolvedor de C++ e quiser alterar a cor usada para as funções, por exemplo, você poderá procurar pelas **Funções de C++** na lista **Exibir itens**.

1. Antes de sair da caixa de diálogo, vamos alterar também a cor dos atributos XML. Na lista **Exibir itens**, role para baixo até **Atributo XML** e selecione-o. Na caixa **Primeiro plano do item**, escolha **Verde-limão**. Escolha **OK** para salvar nossas seleções e fechar a caixa de diálogo.

   Os números de linha agora são uma cor verde-oliva e os atributos XML são verde-limão brilhante. Se você abrir outro tipo de arquivo, como um arquivo de código C++ ou C#, verá que os números de linha também aparecem na cor verde-oliva.

   ![Arquivo XML com novas cores de fonte](media/quickstart-personalize-xml-file-new-colors.png)

Exploramos apenas duas maneiras de personalizar as cores no Visual Studio. Esperamos que você explore as outras opções de personalização na caixa de diálogo **Opções**, para realmente ter um Visual Studio personalizado.

## <a name="see-also"></a>Consulte também

- [Personalizar o editor](../ide/how-to-change-text-case-in-the-editor.md)
- [Visão geral do Visual Studio IDE](../get-started/visual-studio-ide.md)