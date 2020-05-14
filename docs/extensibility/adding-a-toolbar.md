---
title: Adicionando uma barra de ferramentas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740220"
---
# <a name="add-a-toolbar"></a>Adicione uma barra de ferramentas
Este passo a passo mostra como adicionar uma barra de ferramentas ao Visual Studio IDE.

 Uma barra de ferramentas é uma tira horizontal ou vertical que contém botões que estão vinculados a comandos. Dependendo de sua implementação, uma barra de ferramentas no IDE pode ser reposicionada, encaixada em qualquer lado da janela IDE principal ou feita para ficar em frente a outras janelas.

 Além disso, os usuários podem adicionar comandos a uma barra de ferramentas ou removê-los usando a caixa de diálogo **Personalizar.** Normalmente, as barras de ferramentas em VSPackages são personalizáveis pelo usuário. O IDE lida com toda a personalização, e o VSPackage responde a comandos. O VSPackage não precisa saber onde um comando está fisicamente localizado.

 Para obter mais informações sobre menus, consulte [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Crie uma extensão com uma barra de ferramentas
 Crie um projeto `IDEToolbar`VSIX chamado . Adicione um modelo de item de comando de menu chamado **ToolbarTestCommand**. Para obter informações sobre como fazer isso, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Crie uma barra de ferramentas para o IDE

1. Em *ToolbarTestCommandPackage.vsct*, procure a seção Símbolos. No elemento GuidSymbol chamado guidToolbarTestCommandPackageCmdSet, adicione declarações para uma barra de ferramentas e um grupo de barras de ferramentas, da seguinte forma.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Na parte superior da seção Comandos, crie uma seção Menus. Adicione um elemento Menus à seção Menus para definir sua barra de ferramentas.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     As barras de ferramentas não podem ser aninhadas como submenus. Portanto, você não precisa atribuir um grupo de pais. Além disso, você não precisa definir uma prioridade, pois o usuário pode mover barras de ferramentas. Normalmente, a colocação inicial de uma barra de ferramentas é definida programáticamente, mas as alterações subseqüentes pelo usuário são persistidas.

3. Na seção [Grupos,](../extensibility/groups-element.md) após a entrada do grupo existente, defina um elemento [Grupo](../extensibility/group-element.md) para conter os comandos da barra de ferramentas.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Faça o botão aparecer na barra de ferramentas. Na seção Botões, substitua o bloco Pai no botão para a barra de ferramentas. O bloco de botão resultante deve ser assim:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Por padrão, se uma barra de ferramentas não tiver comandos, ela não aparecerá.

5. Compile o projeto e comece a depuração. A instância experimental deve aparecer.

6. Clique com o botão direito do mouse na barra de menus do Visual Studio para obter a lista de barras de ferramentas. Selecione **A barra de ferramentas de teste**.

7. Agora você deve ver sua barra de ferramentas como um ícone à direita do ícone Encontrar em Arquivos. Quando você clica no ícone, você deve ver uma caixa de mensagem que diz **ToolbarTestCommandPackage. Dentro do IDEToolbar.ToolbarTestCommand.MenuItemCallback()**

## <a name="see-also"></a>Confira também
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
