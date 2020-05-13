---
title: Adicionando uma barra de ferramentas a uma janela de ferramentas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740251"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Adicione uma barra de ferramentas a uma janela de ferramenta
Este passo a passo mostra como adicionar uma barra de ferramentas a uma janela de ferramenta.

 Uma barra de ferramentas é uma tira horizontal ou vertical que contém botões ligados a comandos. O comprimento de uma barra de ferramentas em uma janela de ferramenta é sempre o mesmo que a largura ou altura da janela da ferramenta, dependendo de onde a barra de ferramentas está encaixada.

 Ao contrário das barras de ferramentas no IDE, uma barra de ferramentas em uma janela de ferramenta deve ser encaixada e não pode ser movida ou personalizada. Se o VSPackage estiver escrito em umanaged code, a barra de ferramentas pode ser encaixada em qualquer borda.

 Para obter mais informações sobre como adicionar uma barra de ferramentas, consulte [Adicionar uma barra de ferramentas](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalando o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Crie uma barra de ferramentas para uma janela de ferramenta

1. Crie um projeto `TWToolbar` VSIX chamado que tenha um comando de menu chamado **TWTestCommand** e uma janela de ferramenta chamada **TestToolWindow**. Para obter mais informações, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md) e Criar uma [extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md). Você precisa adicionar o modelo de item de comando antes de adicionar o modelo da janela da ferramenta.

2. Em *TWTestCommandPackage.vsct,* procure a seção Símbolos. No nó GuidSymbol chamado guidTWTestCommandPackageCmdSet declare uma barra de ferramentas e um grupo de barras de ferramentas, da seguinte forma.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. Na parte superior `Commands` da seção, crie uma `Menus` seção. Adicione `Menu` um elemento para definir a barra de ferramentas.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Barras de ferramentas não podem ser aninhadas como submenus. Portanto, você não tem que designar um pai. Além disso, você não precisa definir uma prioridade, porque o usuário pode mover barras de ferramentas. Normalmente, a colocação inicial de uma barra de ferramentas é definida programáticamente, mas as alterações subseqüentes pelo usuário são persistidas.

4. Na seção Grupos, defina um grupo para conter os comandos da barra de ferramentas.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Na seção Botões, altere o pai do elemento Button existente para o grupo da barra de ferramentas para que a barra de ferramentas seja exibida.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Por padrão, se uma barra de ferramentas não tiver comandos, ela não aparecerá.

     Como a nova barra de ferramentas não é adicionada automaticamente à janela da ferramenta, a barra de ferramentas deve ser adicionada explicitamente. Isso é abordado na próxima seção.

## <a name="add-the-toolbar-to-the-tool-window"></a>Adicione a barra de ferramentas à janela da ferramenta

1. Em *TWTestCommandPackageGuids.cs* adicionar as seguintes linhas.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. Em *TestToolWindow.cs* adicione a seguinte declaração usando.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. No construtor TestToolWindow adicione a seguinte linha.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Teste a barra de ferramentas na janela da ferramenta

1. Compile o projeto e comece a depuração. A instância experimental do Visual Studio deve aparecer.

2. No **menu Exibir / Outros Windows,** clique em **Testar ferramentaJanela** para exibir a janela da ferramenta.

     Você deve ver uma barra de ferramentas (parece o ícone padrão) no canto superior esquerdo da janela da ferramenta, logo abaixo do título.

3. Na barra de ferramentas, clique no ícone para exibir a mensagem **TWTestCommandPackage Dentro do TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Confira também
- [Adicione uma barra de ferramentas](../extensibility/adding-a-toolbar.md)
