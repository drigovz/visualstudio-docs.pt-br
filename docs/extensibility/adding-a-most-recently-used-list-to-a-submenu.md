---
title: Adicionando uma lista usada mais recentemente a um submenu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740292"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Adicione uma lista usada mais recentemente a um submenu
Este passo a passo se baseia nas demonstrações em [Adicionar um submenu a um menu](../extensibility/adding-a-submenu-to-a-menu.md)e mostra como adicionar uma lista dinâmica a um submenu. A lista dinâmica forma a base para criar uma lista mru usada recentemente.

Uma lista de menus dinâmicos começa com um espaço reservado em um menu. Toda vez que o menu é mostrado, o ambiente de desenvolvimento integrado do Visual Studio (IDE) solicita ao VSPackage todos os comandos que devem ser mostrados no espaço reservado. Uma lista dinâmica pode ocorrer em qualquer lugar de um menu. No entanto, as listas dinâmicas são tipicamente armazenadas e exibidas por si mesmas em submenus ou na parte inferior dos menus. Usando esses padrões de design, você habilita a lista dinâmica de comandos para expandir e contrair sem afetar a posição de outros comandos no menu. Neste passo a passo, a lista de MRU dinâmica é exibida na parte inferior de um submenu existente, separada do resto do submenu por uma linha.

Tecnicamente, uma lista dinâmica também pode ser aplicada a uma barra de ferramentas. No entanto, desencorajamos esse uso porque uma barra de ferramentas deve permanecer inalterada, a menos que o usuário tome medidas específicas para alterá-la.

Este passo a passo cria uma lista mru de quatro itens que mudam sua ordem cada vez que um deles é selecionado (o item selecionado passa para o topo da lista).

Para obter mais informações sobre menus e arquivos *.vsct,* consulte [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Pré-requisitos
Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Criar uma extensão

- Siga os procedimentos em [Adicionar um submenu a um menu](../extensibility/adding-a-submenu-to-a-menu.md) para criar o submenu que é modificado nos procedimentos a seguir.

  Os procedimentos neste passo a passo assumem `TopLevelMenu`que o nome do VSPackage é , que é o nome que é usado em [Adicionar um menu à barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Crie um comando de lista de itens dinâmicos

1. Abrir *TestCommandPackage.vsct*.

2. Na `Symbols` seção, `GuidSymbol` no nó chamado guidTestCommandPackageCmdSet, adicione `MRUListGroup` o `cmdidMRUList` símbolo para o grupo e o comando, da seguinte forma.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. Na `Groups` seção, adicione o grupo declarado após as entradas do grupo existente.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. Na `Buttons` seção, adicione um nó para representar o comando recém-declarado, após as entradas de botão existentes.

    ```csharp
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"
        type="Button" priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />
        <CommandFlag>DynamicItemStart</CommandFlag>
        <Strings>
            <CommandName>cmdidMRUList</CommandName>
            <ButtonText>MRU Placeholder</ButtonText>
        </Strings>
    </Button>
    ```

    O `DynamicItemStart` sinalizador permite que o comando seja gerado dinamicamente.

5. Construa o projeto e comece a depurar para testar a exibição do novo comando.

    No menu **TestMenu,** clique no novo submenu, **Sub Menu**, para exibir o novo comando **MRU Placeholder**. Depois que uma lista de comandos de MRU dinâmica for implementada no próximo procedimento, este rótulo de comando será substituído por essa lista toda vez que o submenu for aberto.

## <a name="filling-the-mru-list"></a>Preenchendo a lista mru

1. Em *TestCommandPackageGuids.cs*, adicione as seguintes linhas após `TestCommandPackageGuids` os IDs de comando existentes na definição de classe.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. Em *TestCommand.cs* adicionar a seguinte declaração usando.

    ```csharp
    using System.Collections;
    ```

3. Adicione o seguinte código no construtor TestCommand após a última chamada AddCommand. O `InitMRUMenu` será definido mais tarde

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Adicione o seguinte código na classe TestCommand. Este código inicializa a lista de strings que representam os itens a serem mostrados na lista MRU.

    ```csharp
    private int numMRUItems = 4;
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;
    private ArrayList mruList;

    private void InitializeMRUList()
    {
        if (null == this.mruList)
        {
            this.mruList = new ArrayList();
            if (null != this.mruList)
            {
                for (int i = 0; i < this.numMRUItems; i++)
                {
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,
                        "Item {0}", i + 1));
                }
            }
        }
    }
    ```

5. Após `InitializeMRUList` o método, `InitMRUMenu` adicione o método. Isso inicializa os comandos do menu da lista MRU.

    ```csharp
    private void InitMRUMenu(OleMenuCommandService mcs)
    {
        InitializeMRUList();
        for (int i = 0; i < this.numMRUItems; i++)
        {
            var cmdID = new CommandID(
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);
            var mc = new OleMenuCommand(
                new EventHandler(OnMRUExec), cmdID);
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);
            mcs.AddCommand(mc);
        }
    }
    ```

    Você deve criar um objeto de comando de menu para todos os itens possíveis na lista MRU. O IDE `OnMRUQueryStatus` chama o método para cada item da lista MRU até que não haja mais itens. No código gerenciado, a única maneira de o IDE saber que não há mais itens é criar todos os itens possíveis primeiro. Se você quiser, você pode marcar itens adicionais `mc.Visible = false;` como não visíveis no início usando depois que o comando menu é criado. Esses itens podem então ser tornados `mc.Visible = true;` visíveis mais tarde usando no `OnMRUQueryStatus` método.

6. Após `InitMRUMenu` o método, `OnMRUQueryStatus` adicione o seguinte método. Este é o manipulador que define o texto para cada item MRU.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Após `OnMRUQueryStatus` o método, `OnMRUExec` adicione o seguinte método. Este é o manipulador para selecionar um item MRU. Este método move o item selecionado para o topo da lista e, em seguida, exibe o item selecionado em uma caixa de mensagem.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
                for (int i = MRUItemIndex; i > 0; i--)
                {
                    this.mruList[i] = this.mruList[i - 1];
                }
                this.mruList[0] = selection;
                System.Windows.Forms.MessageBox.Show(
                    string.Format(CultureInfo.CurrentCulture,
                                  "Selected {0}", selection));
            }
        }
    }

    ```

## <a name="testing-the-mru-list"></a>Testando a lista mru

1. Compile o projeto e comece a depuração.

2. No menu **TestMenu,** clique **em Invocar TestCommand**. Fazendo isso exibe uma caixa de mensagem que indica que o comando foi selecionado.

    > [!NOTE]
    > Esta etapa é necessária para forçar o VSPackage a carregar e exibir corretamente a lista MRU. Se você pular esta etapa, a lista MRU não será exibida.

3. No menu **Menu de teste,** clique **em Sub Menu**. Uma lista de quatro itens é exibida no final do submenu, abaixo de um separador. Quando você clicar **em Item 3**, uma caixa de mensagem deve aparecer e exibir o texto, **Item selecionado 3**. (Se a lista de quatro itens não for exibida, certifique-se de que seguiu as instruções na etapa anterior.)

4. Abra o submenu novamente. Observe que o **Item 3** está agora no topo da lista e os outros itens foram empurrados para baixo em uma posição. Clique **no Item 3** novamente e observe que a caixa de mensagens ainda exibe o **Item 3 selecionado,** o que indica que o texto foi corretamente movido para a nova posição juntamente com a etiqueta de comando.

## <a name="see-also"></a>Confira também
- [Adicionando itens de menu dinamicamente](../extensibility/dynamically-adding-menu-items.md)
