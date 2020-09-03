---
title: MenuCommands vs. OleMenuCommands | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
manager: jillfra
ms.openlocfilehash: 42c471ca924bfded62db32a956a26c07240459eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67624438"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands vs. OleMenuCommands
Você pode criar comandos de menu derivando de um <xref:System.ComponentModel.Design.MenuCommand> objeto de ou para <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> e implementando os manipuladores de eventos apropriados. Na maioria dos casos, você pode usar <xref:System.ComponentModel.Design.MenuCommand> , como o modelo de projeto VSPackage, mas, ocasionalmente, talvez você precise usar <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .  
  
 Os comandos que um VSPackage disponibiliza para o IDE devem estar visíveis e habilitados antes que um usuário possa usá-los. Quando os comandos são criados em um arquivo. vsct usando o modelo de projeto de pacote do Visual Studio, eles são visíveis e habilitados por padrão. A definição de alguns sinalizadores de comando, como `DynamicItemStart` , pode alterar o comportamento padrão. A visibilidade, o status habilitado e outras propriedades de um comando também podem ser alterados no código em tempo de execução acessando o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto que está associado ao comando.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passos, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Locais de modelo para o modelo de pacote do Visual Studio  
 Você pode encontrar o modelo de pacote do Visual Studio na caixa de diálogo **novo projeto** em **Visual Basic/extensibilidade**, **C#/extensibilidade**ou **outros tipos/extensibilidade de projeto**.  
  
## <a name="creating-a-command"></a>Criando um comando  
 Todos os comandos, grupos de comandos, menus, barras de ferramentas e janelas de ferramentas são definidos no arquivo. vsct. Para obter mais informações, consulte [tabela de comandos do Visual Studio (. Vsct) arquivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Se você estiver criando um VSPackage usando o modelo de pacote, selecione **comando de menu** para criar um arquivo. vsct e definir um comando de menu padrão. Para obter mais informações, consulte [criando uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>Para adicionar um comando ao IDE  
  
1. Abra o arquivo. vsct.  
  
2. Na `Symbols` seção, localize o elemento [GuidSymbol](../extensibility/guidsymbol-element.md) que contém os grupos e comandos.  
  
3. Crie um elemento [IDSymbol](../extensibility/idsymbol-element.md) para cada menu, grupo ou comando que você deseja adicionar, conforme mostrado no exemplo a seguir.  
  
   ```xml
   <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
     <IDSymbol name="MyMenuGroup" value="0x1020" />
     <IDSymbol name="cmdidMyCommand" value="0x0100" />
   </GuidSymbol>
   ```
      
    Os `name` atributos dos `GuidSymbol` elementos e `IDSymbol` fornecem o par GUID: ID para cada novo menu, grupo ou comando. O `guid` representa um conjunto de comandos que é definido para seu VSPackage. Você pode definir vários conjuntos de comandos. Cada par GUID: ID deve ser exclusivo.  
  
4. Na seção [botões](../extensibility/buttons-element.md) , crie um elemento [Button](../extensibility/button-element.md) para definir o comando, conforme mostrado no exemplo a seguir.  
  
   ```xml
   <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
     <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
       <CommandName>cmdidMyCommand</CommandName>
       <ButtonText>My Command name</ButtonText>
     </Strings>
   </Button>
   ``` 
     
   1. Defina os `guid` `id` campos e para corresponder ao GUID: ID do novo comando.  
  
   2. Defina o `priority` atributo.  
  
        O `priority` atributo é usado pelo. vsct para determinar o local do botão entre os outros objetos em seu grupo pai.  
  
        Comandos que têm valores de prioridade mais baixos são exibidos acima ou à esquerda de, comandos que têm valores de prioridade mais altos. Valores de prioridade duplicados são permitidos, mas a posição relativa de comandos com prioridade igual é determinada pela ordem em que VSPackages são processados em tempo de execução, e essa ordem não pode ser predeterminada.  
  
        Omitir o `priority` atributo define seu valor como 0.  
  
   3. Defina o `type` atributo. Na maioria dos casos, seu valor será `"Button"` . Para obter descrições de outros tipos de botão válidos, consulte [elemento Button](../extensibility/button-element.md).  
  
5. Na definição do botão, crie um elemento de [cadeia de caracteres](../extensibility/strings-element.md) que contenha um elemento [ButtonText](../extensibility/buttontext-element.md) para conter o nome do menu como ele aparece no IDE e um elemento [CommandName](../extensibility/commandname-element.md) para conter o nome do comando que é usado para acessar o menu na janela de **comando** .  
  
    Se a cadeia de caracteres de texto do botão incluir o caractere ' & ', o usuário poderá abrir o menu pressionando ALT mais o caractere que segue imediatamente o ' & '.  
  
    A adição de um `Tooltip` elemento fará com que o texto contido apareça quando um usuário passar o ponteiro sobre o botão.  
  
6. Adicione um elemento [Icon](../extensibility/icon-element.md) para especificar o ícone, se houver, a ser exibido com o comando. Ícones são necessários para botões em barras de ferramentas, mas não para itens de menu. O `guid` e o `id` do `Icon` elemento devem corresponder aos de um elemento de [bitmap](../extensibility/bitmap-element.md) definido na `Bitmaps` seção.  
  
7. Adicione sinalizadores de comando, conforme apropriado, para alterar a aparência e o comportamento do botão. Para fazer isso, adicione um elemento [CommandFlag](../extensibility/command-flag-element.md) na definição do menu.  
  
8. Defina o grupo pai do comando. O grupo pai pode ser um grupo que você cria, um grupo de outro pacote ou um grupo do IDE. Por exemplo, para adicionar o comando à barra de ferramentas de edição do Visual Studio, ao lado dos botões **comentar** e **Remover comentário** , defina o pai como guidStdEditor: IDG_VS_EDITTOOLBAR_COMMENT. Se o pai for um grupo definido pelo usuário, ele deverá ser o filho de um menu, barra de ferramentas ou janela de ferramentas que aparece no IDE.  
  
    Você pode fazer isso de duas maneiras, dependendo do seu design:  
  
   - No `Button` elemento, crie um elemento [pai](../extensibility/parent-element.md) e defina seus `guid` campos e `id` como o GUID e a ID do grupo que hospedará o comando, também conhecido como o *grupo pai primário*.  
  
        O exemplo a seguir define um comando que será exibido em um menu definido pelo usuário.  
  
       ```xml
       <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
         <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
         <Icon guid="guidImages" id="bmpPic1" />
         <Strings>
           <CommandName>cmdidTestCommand</CommandName>
           <ButtonText>Test Command</ButtonText>
             </Strings>
       </Button>
       ```
      
   - Você pode omitir o `Parent` elemento se o comando for posicionado usando o posicionamento do comando. Crie um elemento [CommandPlacements](../extensibility/commandplacements-element.md) antes da `Symbols` seção e adicione um elemento [CommandPlacement](../extensibility/commandplacement-element.md) que tenha o `guid` e o `id` do comando, a e `priority` um pai, conforme mostrado no exemplo a seguir.  
  
   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
       <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     </CommandPlacement>
   </CommandPlacements>
   ```
      
      Criar vários posicionamentos de comando que têm o mesmo GUID: ID e ter pais diferentes faz com que um menu apareça em vários locais. Para obter mais informações, consulte elemento [CommandPlacements](../extensibility/commandplacements-element.md) .  
  
    Para obter mais informações sobre grupos de comandos e pai, consulte [criando grupos reutilizáveis de botões](../extensibility/creating-reusable-groups-of-buttons.md).  
  
   Neste ponto, o comando ficará visível no IDE, mas não terá nenhuma funcionalidade. Se o comando foi criado pelo modelo de pacote, por padrão ele terá um manipulador de cliques que exibe uma mensagem.  
  
## <a name="handling-the-new-command"></a>Manipulando o novo comando  
 A maioria dos comandos no código gerenciado pode ser tratada pela MPF (estrutura de pacote gerenciada) associando o comando a um <xref:System.ComponentModel.Design.MenuCommand> objeto ou <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto e implementando seus manipuladores de eventos.  
  
 Para o código que usa a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface diretamente para manipulação de comandos, você deve implementar a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface e seus métodos. Os dois métodos mais importantes são <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> .  
  
1. Obtenha a <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> instância, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[ButtonGroup#21](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#21)]  
  
2. Crie um <xref:System.ComponentModel.Design.CommandID> objeto que tenha como seus parâmetros o GUID e a ID do comando a ser manipulado, conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[ButtonGroup#22](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#22)]  
  
     O modelo de pacote do Visual Studio fornece duas coleções `GuidList` e `PkgCmdIDList` , para manter os GUIDs e as IDs de comandos. Eles são preenchidos automaticamente para comandos que são adicionados pelo modelo, mas para comandos que você adiciona manualmente, você também deve adicionar a entrada de ID à `PkgCmdIdList` classe.  
  
     Como alternativa, você pode preencher o <xref:System.ComponentModel.Design.CommandID> objeto usando o valor da cadeia de caracteres bruta do GUID e o valor inteiro da ID.  
  
3. Crie uma instância de um <xref:System.ComponentModel.Design.MenuCommand> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto ou que especifica o método que manipula o comando junto com o <xref:System.ComponentModel.Design.CommandID> , conforme mostrado no exemplo a seguir.  
  
     [!code-csharp[ButtonGroup#23](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#23)]  
  
     O <xref:System.ComponentModel.Design.MenuCommand> é apropriado para comandos estáticos. O item de menu dinâmico exibe os manipuladores de eventos QueryStatus. O <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> adiciona o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> evento, que ocorre quando o menu host do comando é aberto e algumas outras propriedades, como <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> .  
  
     Os comandos criados pelo modelo de pacote são passados por padrão para um <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto no `Initialize()` método da classe de pacote.  
  
4. O <xref:System.ComponentModel.Design.MenuCommand> é apropriado para comandos estáticos. O item de menu dinâmico exibe os manipuladores de eventos QueryStatus. O <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> adiciona o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> evento, que ocorre quando o menu host do comando é aberto e algumas outras propriedades, como <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> .  
  
     Os comandos criados pelo modelo de pacote são passados por padrão para um <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto no `Initialize()` método da classe de pacote. O assistente do Visual Studio implementa o `Initialize` método usando `MenuCommand` . Para exibições de item de menu dinâmico, você deve alterar isso para `OleMenuCommand` , conforme mostrado na próxima etapa. Além disso, para alterar o texto do item de menu, você deve adicionar um sinalizador de comando textchanges ao botão de comando de menu no arquivo. vsct, como é mostrado no exemplo a seguir  
  
    ```xml
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
      
5. Passe o novo comando de menu para o <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> método na <xref:System.ComponentModel.Design.IMenuCommandService> interface. Isso é feito por padrão para comandos criados pelo modelo de pacote, conforme mostrado no exemplo a seguir  
  
     [!code-csharp[ButtonGroup#24](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#24)]  
  
6. Implemente o método que manipula o comando.  
  
#### <a name="to-implement-querystatus"></a>Para implementar o QueryStatus  
  
1. O evento QueryStatus ocorre antes de um comando ser exibido. Isso permite que as propriedades desse comando sejam definidas no manipulador de eventos antes que ele chegue ao usuário. Somente comandos adicionados como <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objetos podem acessar esse método.  
  
    Adicione um `EventHandler` objeto ao <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> evento no <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto que é criado para manipular o comando, conforme mostrado no exemplo a seguir ( `menuItem` é a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> instância).  
  
    [!code-csharp[MenuText#14](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#14)]
    [!code-vb[MenuText#14](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#14)]  
  
    O `EventHandler` objeto recebe o nome de um método que é chamado quando o status do comando de menu é consultado.  
  
2. Implemente o método de manipulador de status de consulta para o comando. O `object` `sender` parâmetro pode ser convertido em um <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto, que é usado para definir os vários atributos do comando de menu, incluindo o texto. A tabela a seguir mostra as propriedades na <xref:System.ComponentModel.Design.MenuCommand> classe (da qual a classe MPF <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> é derivada) que correspondem aos <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> sinalizadores.  
  
   |Propriedade MenuCommand|Sinalizador OLECMDF|  
   |--------------------------|------------------|  
   |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
    Para alterar o texto de um comando de menu, use a <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> propriedade no <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objeto, conforme mostrado no exemplo a seguir.  
  
    [!code-csharp[MenuText#11](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#11)]
    [!code-vb[MenuText#11](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#11)]  
  
   O MPF manipula automaticamente o caso de grupos sem suporte ou desconhecidos. A menos que um comando tenha sido adicionado ao <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> usando o <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> método, não há suporte para o comando.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Manipulando comandos usando a interface IOleCommandTarget  
 Para o código que usa a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface diretamente, o VSPackage deve implementar os <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> métodos e da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Se o VSPackage implementar uma hierarquia de projeto, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> os <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> métodos e da <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface deverão ser implementados em vez disso.  
  
 Os <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> métodos e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> são projetados para receber um único conjunto de comandos `GUID` e uma matriz de IDs de comando como entrada. Recomendamos que o VSPackages dê suporte total a esse conceito de várias IDs em uma chamada. No entanto, desde que um VSPackage não seja chamado de outros VSPackages, você pode pressupor que a matriz de comandos contenha apenas uma ID de comando, pois os <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> métodos e são executados em uma ordem bem definida. Para obter mais informações sobre roteamento, consulte [Roteamento de comandos em VSPackages](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Para o código que usa a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface diretamente para manipulação de comandos, você deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método no VSPackage da seguinte maneira para manipular comandos.  
  
##### <a name="to-implement-the-querystatus-method"></a>Para implementar o método QueryStatus  
  
1. Retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK> comandos válidos.  
  
2. Defina o `cmdf` elemento do `prgCmds` parâmetro.  
  
    O valor do `cmdf` elemento é a União lógica dos valores da <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> enumeração, combinados usando o operador lógico OR ( `|` ).  
  
    Use a enumeração apropriada com base no status do comando:  
  
   - Se o comando tiver suporte:  
  
      `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
   - Se o comando deve ser invisível no momento:  
  
      `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
   - Se o comando for alternado e parecer ter sido clicado:  
  
      `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
      No caso de processamento de comandos hospedados em um menu do tipo `MenuControllerLatched` , o primeiro comando que é marcado pelo `OLECMDF_LATCHED` sinalizador é o comando padrão exibido pelo menu na inicialização. Para obter mais informações sobre `MenuController` tipos de menu, consulte [elemento menu](../extensibility/menu-element.md).  
  
   - Se o comando estiver habilitado no momento:  
  
      `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
   - Se o comando fizer parte de um menu de atalho e estiver oculto por padrão:  
  
      `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
   - Se o comando usar o `TEXTCHANGES` sinalizador, defina o `rgwz` elemento do `pCmdText` parâmetro para o novo texto do comando e defina o `cwActual` elemento do `pCmdText` parâmetro como o tamanho da cadeia de caracteres de comando.  
  
     Para condições de erro, o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método deve tratar os seguintes casos de erro:  
  
   - Se o GUID for desconhecido ou sem suporte, retorne `OLECMDERR_E_UNKNOWNGROUP` .  
  
   - Se o GUID for conhecido, mas a ID do comando for desconhecida ou sem suporte, retorne `OLECMDERR_E_NOTSUPPORTED` .  
  
   A implementação de VSPackage do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método também deve retornar códigos de erro específicos, dependendo se o comando tem suporte e se o comando foi manipulado com êxito.  
  
##### <a name="to-implement-the-exec-method"></a>Para implementar o método Exec  
  
- Se o comando `GUID` for desconhecido, retorne `OLECMDERR_E_UNKNOWNGROUP` .  
  
- Se o `GUID` for conhecido, mas a ID do comando for desconhecida, retorne `OLECMDERR_E_NOTSUPPORTED` .  
  
- Se o `GUID` e a ID de comando corresponderem ao par GUID: ID usado pelo comando no arquivo. vsct, execute o código associado ao comando e retorne <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de esquema XML VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [Estendendo comandos e menus](../extensibility/extending-menus-and-commands.md)
