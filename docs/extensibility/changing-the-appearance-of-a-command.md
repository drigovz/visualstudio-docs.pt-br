---
title: Mudando a aparência de um comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739857"
---
# <a name="change-the-appearance-of-a-command"></a>Alterar a aparência de um comando
Você pode fornecer feedback ao seu usuário alterando a aparência de um comando. Por exemplo, você pode querer que um comando pareça diferente quando ele não estiver disponível. Você pode disponibilizar comandos ou indisponíveis, ocultar ou mostrar ou deschecá-los no menu.

Para alterar a aparência de um comando, execute uma dessas ações:

- Especifique os sinalizadores apropriados na definição de comando no arquivo da tabela de comando.

- Use <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> o serviço.

- Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> a interface e modifique os objetos de comando brutos.

  As etapas a seguir mostram como encontrar e atualizar a aparência de um comando usando o MPF (Managed Package Framework, quadro de pacotes gerenciados).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Para alterar a aparência de um comando de menu

1. Siga as instruções em [Alterar o texto de um comando de menu](../extensibility/changing-the-text-of-a-menu-command.md) para criar um item de menu chamado `New Text`.

2. No arquivo *ChangeMenuText.cs,* adicione a seguinte declaração usando:

    ```csharp
    using System.Security.Permissions;
    ```

3. No arquivo *ChangeMenuTextPackageGuids.cs,* adicione a seguinte linha:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. No *arquivo ChangeMenuText.cs,* substitua o código no método ShowMessageBox pelo seguinte:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Obtenha o comando que deseja <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> atualizar do objeto e, em seguida, defina as propriedades apropriadas no objeto de comando. Por exemplo, o método a seguir torna o comando especificado de um conjunto de comando VSPackage disponível ou indisponível. O código a seguir torna `New Text` o item do menu nomeado indisponível depois de ter sido clicado.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))
            as OleMenuCommandService;
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);
        MenuCommand mc = mcs.FindCommand(newCmdID);
        if (mc != null)
        {
            mc.Enabled = enableCmd;
            cmdUpdated = true;
        }
        return cmdUpdated;
    }
    ```

6. Compile o projeto e comece a depuração. A instância experimental do Visual Studio deve aparecer.

7. No menu **Ferramentas,** clique no **comando Invocar ChangeMenuText.** Neste ponto, o nome do comando é **Invocar ChangeMenuText**, de modo que o manipulador de comando não chame **ChangeMyCommand().**

8. No menu **Ferramentas,** você deve agora ver **Novo Texto**. Clique **em Novo Texto**. O comando deve ser acinzentado.

## <a name="see-also"></a>Confira também
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
- [Como o VSPackages adiciona elementos de interface de usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Estendendo menus e comandos](../extensibility/extending-menus-and-commands.md)
- [Tabela de comando do Visual Studio (. Vsct) Arquivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
