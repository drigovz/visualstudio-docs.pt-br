---
title: 'Walkthrough: Criando um aplicativo de shell isolado básico | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6dc84dd8d9f19012c4d09ba9bfd974ec181b9f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291262"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Walkthrough: Criando um aplicativo de shell isolado básico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial mostra como criar uma solução de shell isolada, personalizar a ajuda sobre a janela de ferramentas e criar um programa de instalação que instala o Shell isolado.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passos, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Para implantar o Shell isolado, você também deve usar o pacote redistribuível do shell do Visual Studio (isolado).  
  
## <a name="creating-an-isolated-shell-solution"></a>Criando uma solução de shell isolado  
 Esta seção mostra como usar o modelo de projeto isolado do shell do Visual Studio para criar uma solução de shell isolada. A solução contém os seguintes projetos:  
  
- O *SolutionName*. O projeto AboutBoxPackage, que permite que você personalize a aparência da caixa ajuda/sobre.  
  
- O projeto ShellExtensionsVSIX, que contém o arquivo Source. Extension. vsixmanifest que define os diferentes componentes do aplicativo de shell isolado.  
  
- O projeto *SolutionName* , que produz o arquivo executável que invoca o aplicativo de shell isolado. Este projeto contém a pasta de personalização do Shell, que permite personalizar a aparência e o comportamento do aplicativo de shell isolado.  
  
- O projeto de interface do usuário do *SolutionName* , que produz um assembly satélite que define comandos de menu ativos e cadeias de caracteres localizáveis.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Para criar uma solução básica de shell isolado  
  
1. Abra o Visual Studio e crie um projeto.  
  
2. Na janela **novo projeto** , expanda **outros tipos de projeto** e, em seguida, **extensibilidade**. Selecione o modelo de projeto **isolado do shell do Visual Studio** .  
  
3. Nomeie o projeto `MyVSShellStub` e especifique um local. Verifique se a opção **criar diretório para solução** está marcada e clique em **OK**.  
  
     A nova solução aparece em **Gerenciador de soluções**.  
  
4. Compile a solução e inicie a depuração do aplicativo de shell isolado.  
  
     O Shell isolado do Visual Studio é exibido. A barra de título lê **MyVSShellStub**. O ícone da barra de título é gerado de \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Personalizando o nome do aplicativo e o ícone  
 Você pode querer marcar seu aplicativo usando o nome da sua empresa e seu logotipo na barra de título. As etapas a seguir mostram como alterar o nome e o ícone que são exibidos na barra de título do aplicativo personalizado alterando o arquivo de definição de pacote, MyVSShellStub. Application. pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Para personalizar o nome do aplicativo e o ícone  
  
1. No projeto MyVSShellStub, abra \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2. Altere o valor do elemento `AppName` para **"AppName" = "editor de música da Fabrikam"**  
  
3. Para alterar o ícone do aplicativo, copie um ícone diferente para o diretório \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Renomeie o arquivo ApplicationIcon. ico existente para ApplicationIcon1. ico. Renomeie o novo arquivo para ApplicationIcon. ico.  
  
4. Compile a solução e inicie a depuração. O IDE de shell isolado é exibido. A barra de título tem o ícone novo ao lado das palavras **Editor de música da Fabrikam**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Personalizando a página inicial do navegador da Web padrão  
 Esta seção mostra como alterar o home page padrão da janela do **navegador da Web** alterando o arquivo de definição de pacote.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Para personalizar o navegador da Web padrão home page  
  
1. No arquivo MyVSShellStub. Application. pkgdef, altere o valor do elemento `DefaultHomePage` para "<https://www.microsoft.com>".  
  
2. Reconstrua o projeto MyVSShellStub.  
  
3. Compile a solução e inicie a depuração.  
  
4. Em **exibição/outras janelas**, clique em **navegador da Web**. A janela do **navegador da Web** exibe o Home Page da Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Removendo o comando Print  
 O arquivo. vsct em um projeto de interface do usuário do Shell isolado consiste em um conjunto de declarações do formulário `<Define name=No_`*elemento*`>`, em que *Element* é um dos menus e comandos padrão do Visual Studio.  
  
 Se uma declaração não tiver um comentário, esse menu ou comando será excluído do Shell isolado. Por outro lado, se uma declaração for comentada, o menu ou comando será incluído no Shell isolado.  
  
 Nas etapas a seguir, você removerá o comentário de comando de impressão no arquivo. vsct.  
  
#### <a name="to-remove-the-print-command"></a>Para remover o comando Imprimir  
  
1. Verifique se o comando **Imprimir** aparece no menu **arquivo** no aplicativo de shell isolado.  
  
2. No projeto MyVSShellStubUI, abra \Resource Files\MyVSShellStubUI.vsct para edição.  
  
3. Remova a marca de comentário desta linha:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. Isso remove o comando Imprimir.  
  
5. Inicie a depuração do aplicativo de shell isolado. Verifique se o comando **arquivo/imprimir** não existe mais.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Removendo recursos do Shell isolado  
 Você pode remover alguns dos pacotes que são carregados com o Visual Studio editando o arquivo. pkgundef se não quiser esses recursos em seu aplicativo de shell isolado personalizado. Você especifica o pacote em uma das subchaves da chave do registro $RootKey $ \Packages.  
  
> [!NOTE]
> Para localizar os GUIDs dos recursos do Visual Studio, consulte [GUIDs de pacote de recursos do Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 O procedimento a seguir mostra como remover o editor de XML do Shell isolado.  
  
#### <a name="to-remove-the-xml-editor"></a>Para remover o editor de XML  
  
1. Abra o arquivo MyVSShellStub. pkgundef na pasta de personalização do shell do projeto MyVSShellStub.  
  
2. Remova a marca de comentário da seguinte linha:  
  
     [$RootKey $ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. Recompile a solução e inicie a depuração do Shell isolado. Abra um arquivo XML, por exemplo, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Verifique se as palavras-chave XML no arquivo não estão coloridas e se a digitação de "<" em uma linha não traz dicas de ferramenta XML.  
  
## <a name="customizing-the-helpabout-box"></a>Personalizando a caixa de ajuda/sobre  
 Você pode personalizar a caixa de ajuda/sobre, que é criada como parte do modelo de projeto de shell isolado.  
  
#### <a name="to-customize-the-company-name"></a>Para personalizar o nome da empresa  
  
1. O nome da empresa, as informações de direitos autorais, a versão do produto e a descrição do produto são encontrados no projeto MyVSShellStub. AboutBoxPackage, no arquivo \Properties\AssemblyInfo.cs. Abra este arquivo.  
  
2. Altere o valor de `AssemblyCompany` para **Fabrikam**, os valores de `AssemblyProduct` e `AssemblyTitle` para o **Editor de música Fabrikam**e o valor de `AssemblyCopyright` para **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3. Para adicionar uma descrição do produto, altere o valor `AssemblyDescription` para **a descrição do editor de música da Fabrikam.** :  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. Inicie a depuração e, no aplicativo de shell isolado, abra a caixa **ajuda/sobre** . Você deve ver as cadeias de caracteres alteradas. O título da caixa de ajuda/sobre é o mesmo que o valor de `AssemblyTitle` em AssemblyInfo.cs.  
  
5. As propriedades da caixa de **ajuda/sobre** em si são encontradas no arquivo MyVSShellStub. AboutBoxPackage\AboutBox.XAML. Para alterar a largura da caixa de ajuda/sobre, vá para o bloco de `AboutDialogStyle` e defina a propriedade `Width` como 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6. Recompile a solução e inicie a depuração do Shell isolado. A caixa de ajuda/sobre deve ser aproximadamente quadrada.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Antes de implantar o aplicativo de shell isolado  
 Seu aplicativo de shell isolado pode ser instalado em qualquer computador que tenha o pacote redistribuível do shell do Visual Studio (isolado). Para obter mais informações sobre o pacote redistribuível, consulte o site de [downloads de extensibilidade do Visual Studio](https://go.microsoft.com/fwlink/?LinkID=119298) .  
  
## <a name="deploying-the-isolated-shell-application"></a>Implantando o aplicativo de shell isolado  
 Você implanta o aplicativo de shell isolado em um computador de destino criando um projeto de instalação. Você deve especificar essas coisas:  
  
- O layout das pastas e dos arquivos no computador de destino.  
  
- As condições de inicialização que garantem que o .NET Framework e o tempo de execução do shell do Visual Studio estejam instalados no computador de destino.  
  
  No procedimento a seguir, você precisará instalar o InstallShield Limited Edition em seu computador.  
  
#### <a name="to-create-the-setup-project"></a>Para criar o projeto de instalação  
  
1. No **Gerenciador de soluções**, clique com o botão direito do mouse no nó da solução e clique em **Adicionar novo projeto**.  
  
2. Na caixa de diálogo **novo projeto** , expanda **outros tipos de projeto** e, em seguida, selecione **instalação e implantação**. Selecione o modelo do InstallShield. Nomeie o novo projeto `MySetup` e clique em **OK**.  
  
3. Se o InstallShield Limited Edition já estiver instalado, vá para a próxima etapa.  
  
    Se o InstallShield Limited Edition ainda não estiver instalado, a página de download do InstallShield será exibida. Siga as instruções para baixar e instalar o produto, escolhendo a versão do InstallShield que é compatível com sua versão do Visual Studio. Você deve decidir se deseja registrar a instalação do InstallShield ou usá-lo como uma avaliação. Você deve reiniciar o Visual Studio depois de concluir a instalação.  
  
   > [!IMPORTANT]
   > Você deve iniciar o Visual Studio como administrador antes de criar um projeto do InstallShield. Se você não fizer isso, receberá um erro ao compilar o projeto.  
  
   As próximas etapas mostram como configurar o projeto de instalação.  
  
> [!IMPORTANT]
> Certifique-se de que você criou a configuração de versão do seu projeto de shell isolado pelo menos uma vez antes de configurar o projeto de instalação.  
  
#### <a name="to-configure-the-setup-project"></a>Para configurar o projeto de instalação  
  
1. Na **Gerenciador de soluções**, no projeto **MySetup** , escolha assistente de **projeto**. Na linha inferior da janela **Assistente de projeto** , escolha **informações do aplicativo**. Insira **Fabrikam** como o nome da sua empresa e **Editor de música da Fabrikam** como o nome do aplicativo. Escolha a seta para frente na parte inferior direita do **Assistente de projeto**.  
  
2. Selecione **Sim** em **o seu aplicativo exige que qualquer software seja instalado no computador?** e, em seguida, selecione **Microsoft .NET pacote completo do Framework 4,5**.  
  
3. Escolha o botão **arquivos de aplicativo** na parte inferior da janela e verifique se a pasta editor de **música Fabrikam** está selecionada.  
  
4. Escolha o botão **Adicionar arquivos** . Na caixa de diálogo **Adicionar arquivos** , adicione os seguintes arquivos da pasta **MyVSShellStub\Release** :  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll.manifest  
  
    4. MyVSShellStub.pkgdef  
  
    5. MyVSShellStub.pkgundef  
  
    6. MyVSShellStub.winprf  
  
    7. Splash. bmp  
  
5. Clique no botão **Adicionar saídas de projeto** e adicione a **saída MyVSShellStub/principal**. Clique em **OK**.  
  
6. No painel esquerdo, em **computador de destino**, clique com o botão direito do mouse no nó do **Editor Fabrikam Music [installdir]** e adicione uma **nova pasta** chamada **extensões**.  
  
7. Clique com o botão direito do mouse no nó **extensões** no painel esquerdo e adicione uma nova pasta chamada **aplicativo**.  
  
8. Selecione a pasta do **aplicativo** e clique no botão **Adicionar saídas do projeto** e selecione a saída primária do projeto MyVSShellStub. AboutBoxPackage.  
  
9. Clique no botão **Adicionar arquivos** e, na pasta \MyVSShellStub\Release\Extensions\Application\, adicione os seguintes arquivos:  
  
    - MyVSShellStub.AboutBoxPackage.pkgdef  
  
    - MyVSShellStub.Application.pkgdef  
  
10. Clique com o botão direito do mouse no nó do **Editor de música Fabrikam [installdir]** no painel esquerdo e adicione uma nova pasta chamada **1033**.  
  
11. Selecione a pasta 1033 e clique no botão **Adicionar saídas do projeto** e selecione a saída primária do projeto MyVSShellStubUI.  
  
12. Mover para a janela de **atalhos do aplicativo** .  
  
13. Clique em **novo** para criar um atalho e selecione **[ProgramFilesFolder] \Fabrikam\Fabrikam música Editor\MyVSShellStub.Primary saída**.  
  
14. Vá para o painel de **entrevista de instalação** .  
  
15. Definir todos os itens como **não**.  
  
16. Em **Gerenciador de soluções**, no projeto MySetup, abra **definir requisitos de configuração e ações \ requisitos**. A janela **requisitos** é aberta.  
  
17. Clique com o botão direito em **requisitos de software do sistema** e selecione **criar nova condição de inicialização**. O **Assistente de pesquisa do sistema** é exibido.  
  
18. No painel **o que você deseja localizar?** , escolha **entrada do registro** na lista suspensa e clique em **Avançar**.  
  
19. No painel **como você deseja procurar por ele?** , selecione **HKEY_LOCAL_MACHINE** como a raiz do registro. Insira **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** para sistemas de 64 bits ou **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** para sistemas de 32 bits e digite **instalar** como o valor do registro. Clique em **Avançar**.  
  
20. No painel **o que você deseja fazer com o valor?** , insira **este produto requer que o redistribuível do shell do Visual Studio 2015 isolado seja instalado.** como o texto de exibição e clique em **concluir**.  
  
21. Reconstrua a solução de shell isolado para criar o projeto de instalação.  
  
     Você pode encontrar o arquivo setup. exe na seguinte pasta:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Testando o programa de instalação  
 Para testar a instalação, copie o arquivo setup. exe para um computador diferente e execute o executável da instalação. Você deve ser capaz de executar o aplicativo de shell isolado.
