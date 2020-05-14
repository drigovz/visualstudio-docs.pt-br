---
title: Implementação de Comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709573"
---
# <a name="command-implementation"></a>Implementação de comando
Para implementar um comando em um VSPackage, você deve executar as seguintes tarefas:

1. No arquivo *.vsct,* configure um grupo de comando e adicione o comando a ele. Para obter mais informações, consulte [arquivos da tabela de comando visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

2. Registre o comando no Visual Studio.

3. Implemente o comando.

As seções a seguir explicam como registrar e implementar comandos.

## <a name="register-commands-with-visual-studio"></a>Registre comandos com o Visual Studio
 Se o seu comando for aparecer em <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> um menu, você deve adicionar o vsPackage e usar como um valor o nome do menu ou seu ID de recurso.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Além disso, você deve registrar <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>o comando com o . Você pode obter este <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> serviço usando o método se <xref:Microsoft.VisualStudio.Shell.Package>o seu VSPackage for derivado de .

```
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
if ( null != mcs )
{
    // Create the command for the menu item.
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );
    mcs.AddCommand( menuItem );
}

```

## <a name="implement-commands"></a>Implementar comandos
 Há várias maneiras de implementar comandos. Se você quiser um comando de menu estático, que é um comando que sempre <xref:System.ComponentModel.Design.MenuCommand> aparece da mesma maneira e no mesmo menu, crie o comando usando como mostrado nos exemplos na seção anterior. Para criar um comando estático, você deve fornecer um manipulador de eventos responsável pela execução do comando. Como o comando está sempre ativado e visível, você não precisa fornecer seu status ao Visual Studio. Se você quiser alterar o status de um comando dependendo de determinadas condições, você pode criar o comando como uma instância da <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe e, em seu construtor, fornecer um manipulador de eventos para executar o comando e um `QueryStatus` manipulador para notificar o Visual Studio quando o status do comando mudar. Você também <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pode implementar como parte de uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> classe de comando ou, você pode implementar se você estiver fornecendo um comando como parte de um projeto. As duas interfaces <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> e a classe têm métodos que notificam o Visual Studio de uma alteração no status de um comando, e outros métodos que fornecem a execução do comando.

 Quando um comando é adicionado ao serviço de comando, ele se torna um de uma cadeia de comandos. Ao implementar os métodos de notificação de status e execução para o comando, tome cuidado para fornecer apenas para esse comando em particular e passar todos os outros casos para os outros comandos da cadeia. Se você não passar o comando (geralmente retornando), <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>o Visual Studio pode parar de funcionar corretamente.

## <a name="querystatus-methods"></a>Métodos de queryStatus
 Se você estiver implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> o método ou o método, verifique se há o GUID do comando ao qual o comando pertence e o ID do comando. Siga estas diretrizes:

- Se o GUID não for reconhecido, a <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>implementação de qualquer método deve retornar .

- Se a implementação de qualquer método reconhecer o GUID, mas <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>não tiver implementado o comando, o método deve retornar .

- Se a implementação de qualquer método reconhecer o GUID e o comando, o método deve `prgCmds` definir o campo <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> de comandos-bandeiras de cada comando (no parâmetro) usando as seguintes bandeiras:

  - `OLECMDF_SUPPORTED`: O comando é suportado.

  - `OLECMDF_INVISIBLE`: O comando não deve ser visível.

  - `OLECMDF_LATCHED`: O comando é alternado e parece ter sido verificado.

  - `OLECMDF_ENABLED`: O comando está habilitado.

  - `OLECMDF_DEFHIDEONCTXTMENU`: O comando deve ser oculto se aparecer em um menu de atalho.

  - `OLECMDF_NINCHED`: O comando é um controlador de menu e não está habilitado, mas sua lista de menus suspensos não está vazia e ainda está disponível. (Esta bandeira raramente é usada.)

- Se o comando foi definido no arquivo `TextChanges` *.vsct* com o sinalizador, defina os seguintes parâmetros:

  - Defina `rgwz` o `pCmdText` elemento do parâmetro para o novo texto do comando.

  - Defina `cwActual` o `pCmdText` elemento do parâmetro para o tamanho da seqüência de comando.

Além disso, certifique-se de que o contexto atual não é uma função de automação, a menos que seu comando seja especificamente destinado a lidar com funções de automação.

Para indicar que você suporta <xref:Microsoft.VisualStudio.VSConstants.S_OK>um comando específico, retorne . Para todos os outros <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>comandos, retorne.

No exemplo a `QueryStatus` seguir, o método primeiro garante que o contexto não seja uma função de automação e, em seguida, encontra o GUID e o ID de comando corretos. O comando em si está definido para ser ativado e suportado. Nenhum outro comando é suportado.

```csharp
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)
        {
            // make the Right command visible
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;
                return VSConstants.S_OK;
            }
        }
        return Constants.OLECMDERR_E_NOTSUPPORTED;
    }
}
```

## <a name="execution-methods"></a>Métodos de execução
 A implementação do `Exec` método `QueryStatus` se assemelha à implementação do método. Primeiro, certifique-se de que o contexto não é uma função de automação. Em seguida, teste para o GUID e o ID de comando. Se o GUID ou o Comando <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>ID não for reconhecido, retorne .

 Para lidar com o comando, execute-o e retorne <xref:Microsoft.VisualStudio.VSConstants.S_OK> se a execução for bem sucedida. Seu comando é responsável pela detecção e notificação de erros; portanto, retorne um código de erro se a execução falhar. O exemplo a seguir demonstra como o método de execução deve ser implementado.

```csharp
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)
        {
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                //execute the command
                return VSConstants.S_OK;
            }
        }
    }
    return Constants.OLECMDERR_E_NOTSUPPORTED;
}
```

## <a name="see-also"></a>Confira também

- [Como o VSPackages adiciona elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
