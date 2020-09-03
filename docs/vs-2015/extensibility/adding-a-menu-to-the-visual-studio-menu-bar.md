---
title: Adicionando um menu à barra de menus | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184935"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Adicionar um menu a barra de menus do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial mostra como adicionar um menu à barra de menus do IDE (ambiente de desenvolvimento integrado) do Visual Studio. A barra de menus do IDE contém categorias de menu, como **arquivo**, **Editar**, **Exibir**, **janela**e **ajuda**.

 Antes de adicionar um novo menu à barra de menus do Visual Studio, considere se os comandos devem ser colocados em um menu existente. Para obter mais informações sobre o posicionamento do comando, consulte [menus e comandos para o Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Os menus são declarados no arquivo. vsct do projeto. Para obter mais informações sobre menus e arquivos. vsct, consulte [comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).

 Ao concluir este passo a passos, você pode criar um menu chamado **TestMenu** que contém um comando.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Criando um projeto VSIX que tem um modelo de item de comando personalizado

1. Crie um projeto VSIX denominado `TopLevelMenu` . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **novo projeto** em extensibilidade do **Visual C#**  /  **Extensibility**.  Para obter mais informações, consulte [criando uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Quando o projeto for aberto, adicione um modelo de item de comando personalizado chamado **TestCommand**. Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar/novo item**. Na caixa de diálogo **Adicionar novo item** , vá para **Visual C#/extensibilidade** e selecione **comando personalizado**. No campo **nome** na parte inferior da janela, altere o nome do arquivo de comando para **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Criando um menu na barra de menus do IDE

#### <a name="to-create-a-menu"></a>Para criar um menu

1. Em **Gerenciador de soluções**, abra TestCommandPackage. vsct.

     No final do arquivo, há um \<Symbols> nó que contém vários \<GuidSymbol> nós. No nó chamado guidTestCommandPackageCmdSet, adicione um novo símbolo, da seguinte maneira:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2. Crie um \<Menus> nó vazio no \<Commands> nó, logo antes de \<Groups> . No \<Menus> nó, adicione um \<Menu> nó, da seguinte maneira:

    ```xml
    <Menus>
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
            <Parent guid="guidSHLMainMenu"
                    id="IDG_VS_MM_TOOLSADDINS" />
            <Strings>
              <ButtonText>TestMenu</ButtonText>
              <CommandName>TestMenu</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Os `guid` `id` valores e do menu especificam o conjunto de comandos e o menu específico no conjunto de comandos.

     Os `guid` `id` valores e do pai posicionam o menu na seção da barra de menus do Visual Studio que contém os menus ferramentas e suplementos.

     O valor da `CommandName` cadeia de caracteres especifica que o texto deve aparecer no item de menu.

3. Na \<Groups> seção, localize \<Group> e altere o \<Parent> elemento para apontar para o menu que acabamos de adicionar:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Isso faz com que o grupo faça parte do novo menu.

4. Localize a seção `Buttons`. Observe que o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelo de pacote gerou um `Button` elemento que tem seu pai definido como `MyMenuGroup` . Como resultado, esse comando será exibido no menu.

## <a name="building-and-testing-the-extension"></a>Criando e testando a extensão

1. Compile o projeto e comece a depuração. Uma instância da instância experimental deve aparecer.

2. A barra de menus na instância experimental deve conter um menu **TestMenu** .

3. No menu **TestMenu** , clique em **invocar comando de teste**.

     Uma caixa de mensagem deve aparecer e exibir a mensagem "TestCommand Package in TopLevelMenu. TestCommand. MenuItemCallback ()". Isso indica que o novo comando funciona.

## <a name="see-also"></a>Consulte Também
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
