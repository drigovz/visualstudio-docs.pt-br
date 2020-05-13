---
title: Criando uma Página de Opções | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739520"
---
# <a name="create-an-options-page"></a>Crie uma página de opções

Este passo a passo cria uma página simples de Ferramentas/Opções que usa uma grade de propriedade para examinar e definir propriedades.

 Para salvar essas propriedades e restaurá-las a partir de um arquivo de configurações, siga essas etapas e, em seguida, consulte [Criar uma categoria de configurações](../extensibility/creating-a-settings-category.md).

 O MPF oferece duas classes para ajudá-lo a criar páginas de opções de ferramentas, a <xref:Microsoft.VisualStudio.Shell.Package> classe e a <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Você cria um VSPackage para fornecer um contêiner `Package` para essas páginas, subclassificando a classe. Você cria cada página de opções de ferramentas, derivando da `DialogPage` classe.

## <a name="prerequisites"></a>Pré-requisitos

 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Crie uma página da grade de opções de ferramentas

 Nesta seção, você cria uma grade de propriedade de opções de ferramentas simples. Você usa esta grade para exibir e alterar o valor de uma propriedade.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Para criar o projeto VSIX e adicionar um VSPackage

1. Toda extensão do Visual Studio começa com um projeto de implantação vsix, que conterá os ativos de extensão. Crie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um projeto `MyToolsOptionsExtension`VSIX chamado . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Projeto Novo** procurando por "vsix".

2. Adicione um VSPackage adicionando um modelo `MyToolsOptionsPackage`de item do Visual Studio Package chamado . No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Na **caixa de diálogo Adicionar novo item,** vá para A > **Extensibilidade** de **Itens Visuais C#** e selecione **Pacote Visual Studio**. No **campo Nome** na parte inferior da caixa `MyToolsOptionsPackage.cs`de diálogo, altere o nome do arquivo para . Para obter mais informações sobre como criar um VSPackage, consulte [Criar uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Para criar a grade de propriedades Tools Options

1. Abra o arquivo *MyToolsOptionsPackage* no editor de códigos.

2. Adicione a seguinte declaração usando.

   ```csharp
   using System.ComponentModel;
   ```

3. Declare `OptionPageGrid` uma classe e <xref:Microsoft.VisualStudio.Shell.DialogPage>a deriva de .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Aplique <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a `VSPackage` à classe para atribuir à classe uma categoria de opções e o nome da página de opções para o OptionPageGrid. O resultado deve ser assim:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Adicione `OptionInteger` uma propriedade `OptionPageGrid` à classe.

    - Aplique <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> a atribuir à propriedade uma categoria de grade de propriedade.

    - Aplique <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> a atribuir à propriedade um nome.

    - Aplique <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> a atribuir à propriedade uma descrição.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > A implementação <xref:Microsoft.VisualStudio.Shell.DialogPage> padrão de propriedades de suporte que possuem conversores apropriados ou que são estruturas ou matrizes que podem ser expandidas para propriedades que possuem conversores apropriados. Para obter uma lista de <xref:System.ComponentModel> conversores, consulte o namespace.

6. Compile o projeto e comece a depuração.

7. Na instância experimental do Visual Studio, no menu **Ferramentas** clique em **Opções**.

     No painel esquerdo, você deve ver **Minha Categoria**. (As categorias de opções estão listadas em ordem alfabética, por isso deve aparecer na metade da lista.) Abra **minha categoria** e clique em My Grid **Page**. A grade de opções aparece no painel direito. A categoria de propriedade é **Minhas Opções**, e o nome da propriedade é **My Integer Option**. A descrição da propriedade, **minha opção inteiro,** aparece na parte inferior do painel. Mude o valor de seu valor inicial de 256 para outra coisa. Clique **em OK**e, em seguida, reabra My Grid **Page**. Você pode ver que o novo valor persiste.

     Sua página de opções também está disponível na caixa de pesquisa do Visual Studio. Na caixa de pesquisa perto do topo do IDE, digite **Minha Categoria** e você verá Minha **categoria -> My Grid Page** listada nos resultados.

## <a name="create-a-tools-options-custom-page"></a>Crie uma página personalizada de opções de ferramentas

 Nesta seção, você cria uma página De opções de ferramentas com uma iu personalizada. Você usa esta página para exibir e alterar o valor de uma propriedade.

1. Abra o arquivo *MyToolsOptionsPackage* no editor de códigos.

2. Adicione a seguinte declaração usando.

    ```csharp
    using System.Windows.Forms;
    ```

3. Adicione `OptionPageCustom` uma aula, `OptionPageGrid` pouco antes da aula. Derivar a `DialogPage`nova classe de .

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. Adicione um atributo GUID. Adicionar uma propriedade OptionString:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. Aplique um <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> segundo na classe VSPackage. Este atributo atribui à classe uma categoria de opções e nome da página de opções.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. Adicione um novo **controle de usuário** chamado MyUserControl ao projeto.

7. Adicione um controle **TextBox** ao controle do usuário.

     Na janela **Propriedades,** na barra de ferramentas, clique no botão **Eventos** e clique duas vezes no evento **Sair.** O novo manipulador de eventos aparece no código *MyUserControl.cs.*

8. Adicione um `OptionsPage` campo `Initialize` público, um método à classe de controle e atualize o manipulador de eventos para definir o valor da opção ao conteúdo da caixa de texto:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     O `optionsPage` campo contém uma `OptionPageCustom` referência à instância dos pais. O `Initialize` método `OptionString` é exibido na **TextBox**. O manipulador de eventos grava o valor `OptionString` atual da **TextBox** para quando o foco sai da **TextBox**.

9. No arquivo de código do pacote, `OptionPageCustom.Window` adicione `OptionPageCustom` uma substituição para a propriedade à `MyUserControl`classe para criar, inicializar e retornar uma instância de . A classe agora deve ser assim:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. Compile e execute o projeto.

11. Na instância experimental, clique em **Opções de** > **ferramentas**.

12. Encontre **minha categoria** e, em seguida, minha página **personalizada**.

13. Alterar o valor de **OptionString**. Clique **em OK**e, em seguida, reabra Minha página **personalizada**. Você pode ver que o novo valor persistiu.

## <a name="access-options"></a>Opções de acesso

 Nesta seção, você obterá o valor de uma opção do VSPackage que hospeda a página Opções de ferramentas associadas. A mesma técnica pode ser usada para obter o valor de qualquer patrimônio público.

1. No arquivo de código do pacote, adicione uma propriedade pública chamada **OptionInteger** à classe **MyToolsOptionsPackage.**

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Este código <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> chama para `OptionPageGrid` criar ou recuperar uma instância. `OptionPageGrid`chamadas <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> para carregar suas opções, que são propriedades públicas.

2. Agora adicione um modelo de item de comando personalizado chamado **MyToolsOptionsCommand** para exibir o valor. Na **caixa de diálogo Adicionar novo item,** vá para A**Extensibilidade** **Visual C#** > e selecione **Comando Personalizado**. No **campo Nome,** na parte inferior da janela, altere o nome do arquivo de comando para *MyToolsOptionsCommand.cs*.

3. No arquivo *MyToolsOptionsCommand,* substitua o corpo `ShowMessageBox` do método do comando pelo seguinte:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Compile o projeto e comece a depuração.

5. Na instância experimental, no menu **Ferramentas,** clique em **Invocar MyToolsOptionsCommand**.

     Uma caixa de mensagem `OptionInteger`exibe o valor atual de .

## <a name="see-also"></a>Confira também

- [Páginas de opções e opções](../extensibility/internals/options-and-options-pages.md)
