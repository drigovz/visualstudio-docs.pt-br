---
title: Definir o tema escuro do Visual Studio e alterar as cores do texto
description: Saiba como alterar o tema de cores padrão do Visual Studio para o modo escuro e alterar as cores de fonte no editor de códigos.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eb7c9bf04e5f38e5138eae6cf6254bb77bbd6230
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916070"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-the-editor"></a>Como: personalizar o IDE do Visual Studio e o editor

Neste artigo de instruções, personalizaremos o tema de cores do Visual Studio a partir do tema azul padrão para o tema escuro. Em seguida, personalizaremos as cores para dois tipos diferentes de texto no editor de código.

::: moniker range="vs-2017"

Se você ainda não instalou o Visual Studio, vá para a página de [downloads do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se você ainda não instalou o Visual Studio, vá para a página de [downloads do Visual Studio](https://visualstudio.microsoft.com/downloads) para instalá-lo gratuitamente.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>Definir o tema de cores para o IDE

O tema de cores padrão da interface do usuário do Visual Studio é chamado **Azul**. Vamos alterar para **Escuro**.

1. Na barra de menus, que é a linha de menus, como **Arquivo** e **Editar**, escolha **Ferramentas** > **Opções**.

1. Na   >  página opções **gerais** do ambiente, altere a seleção de **tema de cores** para **escuro** e, em seguida, escolha **OK**.

   O tema de cores para todo o IDE (ambiente de desenvolvimento) do Visual Studio é alterado para **Escuro**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 no tema escuro](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 no tema escuro](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Você pode instalar temas predefinidos adicionais instalando o **Editor de tema de cores do Visual Studio** na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Depois que você instalar essa ferramenta, temas de cores adicionais serão exibidos na lista suspensa **Tema de cores**.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Você pode criar seus próprios temas instalando o **Designer de tema de cores do Visual Studio** na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

::: moniker-end

## <a name="change-text-colors-in-the-editor"></a>Alterar as cores do texto no editor

Agora, personalizaremos algumas cores de texto do editor. Primeiro, vamos criar um arquivo XML para ver as cores padrão.

1. Na barra de menus, escolha **arquivo**  >  **novo**  >  **arquivo**.

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

Exploramos apenas duas maneiras de personalizar as cores no Visual Studio. Esperamos que você explore as outras opções de personalização na caixa de diálogo [**Opções**](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) para realmente fazer o Visual Studio.

## <a name="see-also"></a>Confira também

- [Como alterar fontes, cores e temas no Visual Studio](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Como alterar maiúsculas e minúsculas no texto no editor](../ide/how-to-change-text-case-in-the-editor.md)
- [Visão geral do IDE do Visual Studio](../get-started/visual-studio-ide.md)
