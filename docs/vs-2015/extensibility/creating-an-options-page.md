---
title: Criando uma página de opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 63
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b5897f6c4463cc5a3c7928a722ed5a0a09e42b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838588"
---
# <a name="creating-an-options-page"></a>Criando uma página de opções
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial cria uma página simples de ferramentas/opções que usa uma grade de propriedades para examinar e definir propriedades.  
  
 Para salvar essas propriedades e restaurá-las de um arquivo de configurações, siga estas etapas e, em seguida, consulte [criando uma categoria de configurações](../extensibility/creating-a-settings-category.md).  
  
 O MPF fornece duas classes para ajudá-lo a criar páginas de opções de ferramentas, a <xref:Microsoft.VisualStudio.Shell.Package> classe e a <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Você cria um VSPackage para fornecer um contêiner para essas páginas por meio da subclasse da classe Package. Você cria cada página de opções de ferramentas derivando da classe DialogPage.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Criando uma página de grade de opções de ferramentas  
 Nesta seção, você criará uma grade de propriedades de opções de ferramentas simples. Use essa grade para exibir e alterar o valor de uma propriedade.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Para criar o projeto VSIX e adicionar um VSPackage  
  
1. Cada extensão do Visual Studio começa com um projeto de implantação VSIX que conterá os ativos de extensão. Crie um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeto VSIX denominado `MyToolsOptionsExtension` . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **novo projeto** em **Visual C#/extensibilidade**.  
  
2. Adicione um VSPackage adicionando um modelo de item de pacote do Visual Studio denominado `MyToolsOptionsPackage` . Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar/novo item**. Na **caixa de diálogo Adicionar novo item**, vá para **itens/extensibilidade do Visual C#** e selecione **pacote do Visual Studio**. No campo **nome** na parte inferior da caixa de diálogo, altere o nome do arquivo para `MyToolsOptionsPackage.cs` . Para obter mais informações sobre como criar um VSPackage, consulte [criando uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Para criar a grade de propriedades opções de ferramentas  
  
1. Abra o arquivo MyToolsOptionsPackage no editor de código.  
  
2. Adicione a seguinte instrução using.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3. Declare uma classe OptionPageGrid e derive-a de <xref:Microsoft.VisualStudio.Shell.DialogPage> .  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4. Aplique um <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à classe VSPackage para atribuir à classe um nome de página de opções e uma categoria de opções para o OptionPageGrid. O resultado deve ser assim:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5. Adicione uma `OptionInteger` Propriedade à `OptionPageGrid` classe.  
  
    - Aplique um <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> para atribuir à propriedade uma categoria de grade de propriedade.  
  
    - Aplique um <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> para atribuir à propriedade um nome.  
  
    - Aplique um <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> para atribuir à propriedade uma descrição.  
  
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
    > A implementação padrão do <xref:Microsoft.VisualStudio.Shell.DialogPage> oferece suporte a propriedades que têm conversores apropriados ou que são estruturas ou matrizes que podem ser expandidas em propriedades que têm os conversores apropriados. Para obter uma lista de conversores, consulte o <xref:System.ComponentModel> namespace.  
  
6. Compile o projeto e comece a depuração.  
  
7. Na instância experimental do Visual Studio, no menu **ferramentas** , clique em **Opções**.  
  
     No painel esquerdo, você deve ver **minha categoria**. (As categorias de opções são listadas em ordem alfabética, portanto, deve aparecer aproximadamente na metade da lista.) Abra **minha categoria** e, em seguida, clique em **minha página de grade**. A grade de opções aparece no painel direito. A categoria de propriedade é **minhas opções**e o nome da propriedade é **minha opção de inteiro**. A descrição da propriedade, **minha opção de inteiro**, aparece na parte inferior do painel. Altere o valor de seu valor inicial de 256 para outra coisa. Clique em **OK**e reabra **minha página de grade**. Você pode ver que o novo valor persiste.  
  
     Sua página de opções também está disponível por meio do início rápido do Visual Studio. Na janela início rápido no canto superior direito do IDE, digite **minha categoria** e você verá **minha categoria – > minha página de grade** listada na lista suspensa.  
  
## <a name="creating-a-tools-options-custom-page"></a>Criando uma página personalizada de opções de ferramentas  
 Nesta seção, você cria uma página de opções de ferramentas com uma interface do usuário personalizada. Você usa essa página para exibir e alterar o valor de uma propriedade.  
  
1. Abra o arquivo MyToolsOptionsPackage no editor de código.  
  
2. Adicione a seguinte instrução using.  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3. Adicione uma `OptionPageCustom` classe, logo antes da `OptionPageGrid` classe. Derive a nova classe de `DialogPage` .  
  
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
  
4. Adicione um atributo GUID. Adicione uma propriedade Optionstring:  
  
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
  
5. Aplique um segundo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à classe VSPackage. Esse atributo atribui a classe a uma categoria de opções e o nome da página de opções.  
  
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
  
7. Adicione um controle **TextBox** ao controle de usuário.  
  
     Na janela **Propriedades** , na barra de ferramentas, clique no botão **eventos** e clique duas vezes no evento **sair** . O novo manipulador de eventos aparece no código MyUserControl.cs.  
  
8. Adicione um `OptionsPage` campo público, um `Initialize` método à classe de controle e atualize o manipulador de eventos para definir o valor da opção como o conteúdo da caixa de texto:  
  
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
  
     O `optionsPage` campo contém uma referência à instância pai `OptionPageCustom` . O `Initialize` método é exibido `OptionString` na **caixa de texto**. O manipulador de eventos grava o valor atual da **caixa de texto** em `OptionString` quando o foco deixa a **caixa de texto**.  
  
9. No arquivo de código do pacote, adicione uma substituição para a `OptionPageCustom.Window` Propriedade à classe OptionPageCustom para criar, inicializar e retornar uma instância do `MyUserControl` . A classe agora deve se parecer com esta:  
  
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
  
11. Na instância experimental, clique em **ferramentas/opções**.  
  
12. Localizar **minha categoria** e, em seguida, **minha página personalizada**.  
  
13. Altere o valor de **optionstring**. Clique em **OK**e reabra **minha página personalizada**. Você pode ver que o novo valor foi persistido.  
  
## <a name="accessing-options"></a>Opções de acesso  
 Nesta seção, você obtém o valor de uma opção do VSPackage que hospeda a página de opções de ferramentas associadas. A mesma técnica pode ser usada para obter o valor de qualquer propriedade pública.  
  
1. No arquivo de código do pacote, adicione uma propriedade pública chamada **OptionInteger** à classe **MyToolsOptionsPackage** .  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Esse código chama <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> a criação ou recuperação de uma `OptionPageGrid` instância. `OptionPageGrid` chama <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> para carregar suas opções, que são propriedades públicas.  
  
2. Agora, adicione um modelo de item de comando personalizado chamado **MyToolsOptionsCommand** para exibir o valor. Na caixa de diálogo **Adicionar novo item** , vá para **Visual C#/extensibilidade** e selecione **comando personalizado**. No campo **nome** na parte inferior da janela, altere o nome do arquivo de comando para **MyToolsOptionsCommand.cs**.  
  
3. No arquivo MyToolsOptionsCommand, substitua o corpo do método do comando `ShowMessageBox` pelo seguinte:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4. Compile o projeto e comece a depuração.  
  
5. Na instância experimental, no menu **ferramentas** , clique em **invocar MyToolsOptionsCommand**.  
  
     Uma caixa de mensagem exibe o valor atual de `OptionInteger` .  
  
## <a name="see-also"></a>Consulte Também  
 [Opções e páginas de opções](../extensibility/internals/options-and-options-pages.md)
