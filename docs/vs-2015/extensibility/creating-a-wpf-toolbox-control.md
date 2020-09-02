---
title: Criando um controle de caixa de ferramentas do WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 768d9747635f2106d16f755db6799e356c890838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197444"
---
# <a name="creating-a-wpf-toolbox-control"></a>Criando um controle de caixa de ferramentas do WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O modelo de controle de caixa de ferramentas do WPF (Windows Presentation Framework) permite criar controles WPF que são adicionados automaticamente à **caixa de ferramentas** quando a extensão é instalada. Este tópico mostra como usar o modelo para criar um controle de **caixa de ferramentas** que você pode distribuir para outros usuários.  
  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Criando um controle de caixa de ferramentas do WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Criar uma extensão com um controle de caixa de ferramentas do WPF  
  
1. Crie um projeto VSIX denominado `MyToolboxControl` . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **novo projeto** em **Visual C#/extensibilidade**.  
  
2. Quando o projeto for aberto, adicione um modelo de item de **controle da caixa de ferramentas do WPF** denominado `MyToolboxControl` . Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar/novo item**. Na caixa de diálogo **Adicionar novo item** , vá para **Visual C#/extensibilidade** e selecione **controle de caixa de ferramentas WPF**. No campo **nome** na parte inferior da janela, altere o nome do arquivo de comando para `MyToolboxControl.cs` .  
  
     Agora, a solução contém um controle de usuário, um `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> que adiciona o controle à **caixa de ferramentas**e uma entrada de ativo **Microsoft. VisualStudio. ToolboxControl** no manifesto do VSIX para implantação.  
  
#### <a name="to-create-the-control-ui"></a>Para criar a interface do usuário do controle  
  
1. Abra MyToolboxControl. XAML no designer.  
  
     O designer mostra um <xref:System.Windows.Controls.Grid> controle que contém um <xref:System.Windows.Controls.Button> controle.  
  
2. Organize o layout da grade. Quando você seleciona o <xref:System.Windows.Controls.Grid> controle, as barras de controle azuis aparecem nas bordas superior e esquerda da grade. Você pode adicionar linhas e colunas à grade clicando nas barras.  
  
3. Adicione controles filho à grade. Você pode posicionar um controle filho arrastando-o da **caixa de ferramentas** para uma seção da grade ou definindo seus `Grid.Row` atributos e `Grid.Column` no XAML. O exemplo a seguir adiciona dois rótulos na linha superior da grade e um botão na segunda linha.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Renomeando o controle  
 Por padrão, seu controle aparecerá na **caixa de ferramentas** como **MyToolboxControl** em um grupo chamado **MyToolboxControl. MyToolboxControl**. Você pode alterar esses nomes no arquivo MyToolboxControl.xaml.cs.  
  
1. Abra MyToolboxControl.xaml.cs na exibição de código.  
  
2. Localize a classe MyToolboxControl e renomeie-a como TestControl. (A maneira mais rápida de fazer isso é renomear a classe e, em seguida, selecionar **renomear** no menu de contexto e concluir as etapas. (Para obter mais informações sobre o comando **renomear** , consulte [refatoração Renomear (C#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3. Vá para o `ProvideToolboxControl` atributo e altere o valor do primeiro parâmetro para **teste**. Esse é o nome do grupo que conterá o controle na caixa de **ferramentas**.  
  
     O código resultante deve ter a seguinte aparência:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Criação, teste e implantação  
 Ao depurar o projeto, você deve encontrar o controle instalado na caixa de **ferramentas** da instância experimental do Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Para compilar e testar o controle  
  
1. Recompile o projeto e inicie a depuração.  
  
2. Na nova instância do Visual Studio, crie um projeto de aplicativo WPF. Verifique se o Designer XAML está aberto.  
  
3. Localize seu controle na **caixa de ferramentas** e arraste-o para a superfície de design.  
  
4. Inicie a depuração do aplicativo do WPF.  
  
5. Verifique se o controle é exibido.  
  
#### <a name="to-deploy-the-control"></a>Para implantar o controle  
  
1. Depois de criar o projeto testado, você pode encontrar o arquivo. vsix na pasta \bin\debug\ do projeto.  
  
2. Você pode instalá-lo em um computador local clicando duas vezes no arquivo. vsix e seguindo o procedimento de instalação. Para desinstalar o controle, acesse **ferramentas/extensões e atualizações** , procure a extensão de controle e clique em **desinstalar**.  
  
3. Carregue o arquivo. vsix em uma rede ou em um site da Web.  
  
     Se você carregar o arquivo no site da [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , outros usuários poderão usar **ferramentas/extensões e atualizações** no Visual Studio para localizar o controle online e instalá-lo.
