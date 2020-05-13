---
title: Criando um controle de caixa de ferramentas do Windows Forms | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739589"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Crie um controle de caixa de ferramentas do Windows Forms

O modelo de item de controle de caixa de ferramentas do Windows Forms que está incluído no Visual Studio Extensibility Tools (VS SDK), permite criar um controle **de caixa de ferramentas** que é adicionado automaticamente quando a extensão é instalada. Este passo a passo mostra como usar o modelo para criar um controle de contador simples que você pode distribuir para outros usuários.

## <a name="prerequisites"></a>Pré-requisitos

A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Crie o controle da caixa de ferramentas

O modelo de controle de caixa de ferramentas do Windows Forms cria um controle de usuário indefinido e fornece todas as funcionalidades necessárias para adicionar o controle à **caixa de ferramentas**.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Crie uma extensão com um Controle de caixa de ferramentas do Windows Forms

1. Crie um projeto `MyWinFormsControl`VSIX chamado . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Novo Projeto,** procurando por "vsix".

2. Quando o projeto for aberto, adicione um modelo de item **de controle de caixa de ferramentas** do Windows Forms nomeado `Counter`. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Na caixa de diálogo **Adicionar novo item,** vá para A**Extensibilidade** **Visual C#** > e selecione **Controle de caixa de ferramentas do Windows Forms**

3. Isso adiciona um controle `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> do usuário, um para colocar o controle na **caixa de ferramentas**e uma entrada **microsoft.VisualStudio.ToolboxControl** Asset no manifesto VSIX para implantação.

### <a name="build-a-user-interface-for-the-control"></a>Construa uma interface de usuário para o controle

O `Counter` controle requer dois controles <xref:System.Windows.Forms.Label> de criança: a <xref:System.Windows.Forms.Button> para exibir a contagem atual e a de redefinir a contagem para 0. Nenhum outro controle infantil é necessário porque os chamadores aumentarão o contador programáticamente.

#### <a name="to-build-the-user-interface"></a>Para construir a interface do usuário

1. No **Solution Explorer,** clique duas vezes *em Counter.cs* para abri-lo no designer.

2. Remova o **Clique Aqui !** botão que é incluído por padrão quando você adiciona o modelo de item controle de caixa de ferramentas do Windows Forms.

3. Da **caixa de ferramentas,** arraste um `Label` controle e, em seguida, um `Button` controle abaixo dele para a superfície de projeto.

4. Redimensione o controle geral do usuário para 150, 50 pixels e redimensione o controle do botão para 50, 20 pixels.

5. Na janela **Propriedades,** defina os seguintes valores para os controles na superfície do projeto.

    |Control|Propriedade|Valor|
    |-------------|--------------|-----------|
    |`Label1`|**Texto**|""|
    |`Button1`|**Nome**|Btnreset|
    |`Button1`|**Texto**|Redefinir|

### <a name="code-the-user-control"></a>Código o controle do usuário

O `Counter` controle exporá um método para incrementar o contador, um evento a ser levantado sempre que o contador for incrementado, um botão **Redefinir** e três propriedades para armazenar a contagem atual, o texto do display e se mostrar ou ocultar o botão **Redefinir.** O `ProvideToolboxControl` atributo determina onde na `Counter` Caixa de **Ferramentas** o controle será exibido.

#### <a name="to-code-the-user-control"></a>Para codificar o controle do usuário

1. Clique duas vezes no formulário para abrir seu manipulador de eventos de carga na janela de código.

2. Acima do método manipulador de eventos, na classe de controle crie um inteiro para armazenar o valor do contador e uma string para armazenar o texto de exibição como mostrado no exemplo a seguir.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Crie as seguintes declarações de propriedade pública.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Os chamadores podem acessar essas propriedades para obter e definir o texto de exibição do contador e para mostrar ou ocultar o botão **Redefinir.** Os chamadores podem obter o `Value` valor atual da propriedade somente leitura, mas não podem definir o valor diretamente.

4. Coloque o seguinte `Load` código no evento para o controle.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Definir o texto <xref:System.Windows.Forms.UserControl.Load> do **Rótulo** no evento permite que as propriedades de destino sejam carregadas antes de seus valores serem aplicados. Definir o **texto do rótulo** na construtora resultaria em um **rótulo**vazio .

5. Crie o seguinte método público para incrementar o contador.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Adicione uma declaração para o `Incremented` evento à classe de controle.

    ```csharp
    public event EventHandler Incremented;
    ```

    Os chamadores podem adicionar manipuladores a este evento para responder a alterações no valor do contador.

7. Retorne à exibição de design e clique `btnReset_Click` duas vezes no botão **Redefinir** para gerar o manipulador de eventos e, em seguida, preencha-o como mostrado no exemplo a seguir.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Imediatamente acima da definição de `ProvideToolboxControl` classe, na declaração de atributo, alterar o valor do primeiro parâmetro de `"MyWinFormsControl.Counter"` para `"General"`. Isso define o nome do grupo de itens que hospedará o controle na **caixa de ferramentas**.

    O exemplo a `ProvideToolboxControl` seguir mostra o atributo e a definição de classe ajustada.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Testar o controle

 Para testar um controle **toolbox,** primeiro teste-o no ambiente de desenvolvimento e, em seguida, teste-o em um aplicativo compilado.

#### <a name="to-test-the-control"></a>Para testar o controle

1. Pressione **F5** para **iniciar a depuração**.

    Este comando constrói o projeto e abre uma segunda instância experimental do Visual Studio que tem o controle instalado.

2. Na instância experimental do Visual Studio, crie um projeto **de aplicativo de formulários do Windows.**

3. No **Solution Explorer,** clique duas vezes *em Form1.cs* para abri-lo no designer se ele ainda não estiver aberto.

4. Na **caixa de ferramentas,** o `Counter` controle deve ser exibido na seção **Geral.**

5. Arraste `Counter` um controle para o formulário e selecione-o. As `Value` `Message`propriedades `ShowReset` serão exibidas na janela **Propriedades,** juntamente com as <xref:System.Windows.Forms.UserControl>propriedades herdadas de .

6. Defina a propriedade `Message` como `Count:`.

7. Arraste <xref:System.Windows.Forms.Button> um controle para o formulário e, em seguida, defina as propriedades de nome e texto do botão para `Test`.

8. Clique duas vezes no botão para abrir *Form1.cs* na visualização de código e criar um manipulador de cliques.

9. No manipulador de `counter1.Increment()`cliques, ligue .

10. Na função construtor, após a `InitializeComponent`chamada `counter1``.``Incremented +=` para , digite e, em seguida, **pressione Tab** duas vezes.

    O Visual Studio gera um `counter1.Incremented` manipulador de nível de formulário para o evento.

11. Destaque `Throw` a declaração no `mbox`manipulador de eventos, digite e pressione **Tab** duas vezes para gerar uma caixa de mensagem a partir do trecho de código mbox.

12. Na próxima linha, adicione `if` / `else` o bloco seguinte para definir a visibilidade do botão **Reset.**

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Pressione **F5**.

    O formulário abre. O `Counter` controle exibe o texto a seguir.

    **Contagem: 0**

14. Clique em **Testar**.

    O contador incrementa e o Visual Studio exibe uma caixa de mensagens.

15. Feche a caixa de mensagens.

    O botão **Reset** desaparece.

16. Clique **em Testar** até que o contador atinja **5** fechando as caixas de mensagem todas as vezes.

    O botão **Reset** reaparece.

17. Clique em **redefinir**.

    O contador reinicia para **0**.

## <a name="next-steps"></a>Próximas etapas

Quando você cria um controle **de caixa de ferramentas,** o Visual Studio cria um arquivo chamado *ProjectName.vsix* na pasta \bin\debug\ do seu projeto. Você pode implantar o controle enviando o arquivo *.vsix* para uma rede ou para um site da Web. Quando um usuário abre o arquivo *.vsix,* o controle é instalado e adicionado à **Caixa de Ferramentas** do Visual Studio no computador do usuário. Alternativamente, você pode carregar o arquivo *.vsix* para [o Visual Studio Marketplace](https://marketplace.visualstudio.com/) para que os usuários possam encontrá-lo navegando na caixa de diálogo**Extensões e Atualizações** de **Ferramentas.** > 

## <a name="see-also"></a>Confira também

- [Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Criar um controle de caixa de ferramentas WPF](../extensibility/creating-a-wpf-toolbox-control.md)
- [Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Noções básicas de desenvolvimento de controle do Windows Forms](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
