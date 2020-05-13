---
title: Criando um controle wpf toolbox | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739573"
---
# <a name="create-a-wpf-toolbox-control"></a>Criar um controle de caixa de ferramentas WPF

O modelo de controle de caixa de ferramentas Do WPF (Windows Presentation Framework) permite criar controles WPF que são adicionados automaticamente à **caixa de ferramentas** quando a extensão é instalada. Este passo a passo mostra como usar o modelo para criar um controle **toolbox** que você pode distribuir para outros usuários.

A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Crie o controle da caixa de ferramentas

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Crie uma extensão com um controle wpf toolbox

1. Crie um projeto `MyToolboxControl`VSIX chamado . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Projeto Novo** procurando por "vsix".

2. Quando o projeto for aberto, adicione um modelo de item **de controle de caixa de ferramentas WPF** chamado `MyToolboxControl`. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Na **caixa de diálogo Adicionar novo item,** vá para A**Extensibilidade** **Visual C#** > e selecione **Controle de caixa de ferramentas WPF**. No **campo Nome,** na parte inferior da janela, altere o nome do arquivo de comando para *MyToolboxControl.cs*.

    A solução agora contém um `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> controle de usuário, um que adiciona o controle à **caixa de ferramentas**e uma entrada **microsoft.VisualStudio.ToolboxControl** Asset no manifesto VSIX para implantação.

#### <a name="to-create-the-control-ui"></a>Para criar a ui de controle

1. Abra *myToolboxControl.xaml* no designer.

    O designer <xref:System.Windows.Controls.Grid> mostra um <xref:System.Windows.Controls.Button> controle que contém um controle.

2. Organize o layout da grade. Quando você <xref:System.Windows.Controls.Grid> seleciona o controle, as barras de controle azuis aparecem nas bordas superior e esquerda da grade. Você pode adicionar linhas e colunas à grade clicando nas barras.

3. Adicione controles de crianças à rede. Você pode posicionar um controle de criança arrastando-o da **caixa** de `Grid.Row` `Grid.Column` ferramentas para uma seção da grade, ou definindo seus atributos no XAML. O exemplo a seguir adiciona duas etiquetas na linha superior da grade e um botão na segunda linha.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Renomeando o controle

 Por padrão, seu controle aparecerá na **caixa de ferramentas** como **MyToolboxControl** em um grupo chamado **MyToolboxControl.MyToolboxControl**. Você pode alterar esses nomes no arquivo *MyToolboxControl.xaml.cs.*

1. Abra *MyToolboxControl.xaml.cs* na exibição do código.

2. Encontre `MyToolboxControl` a classe e renomeie-a para TestControl. (A maneira mais rápida de fazer isso é renomear a classe e, em seguida, selecionar **Renomear** no menu de contexto e completar as etapas. (Para obter mais informações sobre o comando **Renomear,** consulte [Refatoração (C#)](../ide/reference/rename.md).)

3. Vá para `ProvideToolboxControl` o atributo e altere o valor do primeiro parâmetro para **Testar**. Este é o nome do grupo que conterá o controle na **caixa de ferramentas**.

    O código resultante deve ser assim:

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

## <a name="build-test-and-deployment"></a>Construção, teste e implantação

 Ao depurar o projeto, você deve encontrar o controle instalado na caixa de **ferramentas** da instância experimental do Visual Studio.

### <a name="to-build-and-test-the-control"></a>Para construir e testar o controle

1. Reconstrua o projeto e comece a depurar.

2. Na nova instância do Visual Studio, crie um projeto de aplicativo WPF. Certifique-se de que o XAML Designer está aberto.

3. Encontre seu controle na **caixa de ferramentas** e arraste-o para a superfície do projeto.

4. Comece a depurar o aplicativo WPF.

5. Verifique se seu controle é exibido.

### <a name="to-deploy-the-control"></a>Para implantar o controle

1. Depois de construir o projeto testado, você pode encontrar o arquivo\* *.vsix* na pasta *\bin\debug do projeto.

2. Você pode instalá-lo em um computador local clicando duas vezes no arquivo *.vsix* e seguindo o procedimento de instalação. Para desinstalar o controle, vá para**Extensões e Atualizações de** **Ferramentas** > e procure a extensão de controle e clique em **Desinstalar**.

3. Faça upload do arquivo *.vsix* para uma rede ou para um site da Web.

    Se você carregar o arquivo para o site [do Visual Studio Marketplace,](https://marketplace.visualstudio.com/) outros usuários podem usar**extensões e atualizações de** **ferramentas** > no Visual Studio para encontrar o controle on-line e instalá-lo.
