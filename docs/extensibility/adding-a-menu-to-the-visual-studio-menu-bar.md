---
title: Adicionando um menu à Barra de Menus do Visual Studio | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740317"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Adicione um menu à barra de menus do Visual Studio

Este passo a passo mostra como adicionar um menu à barra de menus do ambiente de desenvolvimento integrado visual studio (IDE). A barra de menu iDE contém categorias de menu, como **Arquivo,** **Edição,** **Exibição,** **Janela**e **Ajuda**.

Antes de adicionar um novo menu à barra de menus do Visual Studio, considere se seus comandos devem ser colocados dentro de um menu existente. Para obter mais informações sobre a colocação de [comandos, consulte Menus e comandos para Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Os menus são declarados no arquivo *.vsct* do projeto. Para obter mais informações sobre menus e arquivos *.vsct,* consulte [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).

Ao completar este passo a passo, você pode criar um menu chamado **TestMenu** que contém um comando.

> [!NOTE]
> No VS 2019, menus de nível superior contribuídos por extensões são colocados no menu **Extensões.**

## <a name="prerequisites"></a>Pré-requisitos

A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Crie um projeto VSIX que tenha um modelo de item de comando personalizado

1. Crie um projeto `TopLevelMenu`VSIX chamado . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Projeto Novo** procurando por "vsix".  Para obter mais informações, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Quando o projeto for aberto, adicione um modelo de item de comando personalizado chamado **TestCommand**. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** >  **novo item**. Na **caixa de diálogo Adicionar novo item,** vá para **Visual C# / Extensibility** e selecione **Comando Personalizado**. No **campo Nome,** na parte inferior da janela, altere o nome do arquivo de comando para *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Crie um menu na barra de menus do IDE

::: moniker range="vs-2017"

1. No **Solution Explorer,** abra *TestCommandPackage.vsct*.

    No final do arquivo, há \<um nó de> \<símbolos que contém vários nostes> GuidSymbol. No nó chamado guidTestCommandPackageCmdSet, adicione um novo símbolo, da seguinte forma:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Crie um \<nó de> \<menus vazio no nó \<Comandos>, pouco antes de Grupos>. No \<nó Menus>, \<adicione um nó Menu>, da seguinte forma:

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

    Os `guid` `id` valores do menu especificam o conjunto de comandos e o menu específico no conjunto de comandos.

    Os `guid` `id` valores do pai posicionam o menu na seção da barra de menus do Visual Studio que contém os menus Ferramentas e Add-ins.

    O valor `CommandName` da seqüência especifica que o texto deve aparecer no item do menu.

3. Na \<seção Grupos>, encontre o> de \<grupo e altere o \<elemento> Pai para apontar para o menu que acabamos de adicionar:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Isso faz do grupo parte do novo menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. No **Solution Explorer,** abra *TopLevelMenuPackage.vsct*.

    No final do arquivo, há \<um nó de> \<símbolos que contém vários nostes> GuidSymbol. No nó chamado guidTopLevelMenuPackageCmdSet, adicione um novo símbolo, da seguinte forma:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Crie um \<nó de> \<menus vazio no nó \<Comandos>, pouco antes de Grupos>. No \<nó Menus>, \<adicione um nó Menu>, da seguinte forma:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    Os `guid` `id` valores do menu especificam o conjunto de comandos e o menu específico no conjunto de comandos.

    Os `guid` `id` valores do pai posicionam o menu na seção da barra de menus do Visual Studio que contém os menus Ferramentas e Add-ins.

    O valor `CommandName` da seqüência especifica que o texto deve aparecer no item do menu.

3. Na \<seção Grupos>, encontre o> de \<grupo e altere o \<elemento> Pai para apontar para o menu que acabamos de adicionar:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Isso faz do grupo parte do novo menu.

::: moniker-end

4. Localize a seção `Buttons`. Observe que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o modelo `Button` Pacote gerou um elemento `MyMenuGroup`que tem seu pai definido como . Como resultado, este comando aparece em seu menu.

## <a name="build-and-test-the-extension"></a>Construir e testar a extensão

1. Compile o projeto e comece a depuração. Um exemplo da instância experimental deve aparecer.

::: moniker range="vs-2017"

2. A barra de menu na instância experimental deve conter um menu **TestMenu.**

::: moniker-end

::: moniker range=">=vs-2019"

2. O menu **Extensões** na instância experimental deve conter um menu **TestMenu.**

::: moniker-end

3. No menu **TestMenu,** clique **em Invocar comando de teste**.

     Uma caixa de mensagens deve aparecer e exibir a mensagem "TestCommand Package Inside TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>Confira também

- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
