---
title: Estender as janelas Propriedades, Lista de Tarefas, Saída, Opções
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711631"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Estender as janelas Propriedades, Lista de Tarefas, Saída e Opções
Você pode acessar qualquer janela de ferramenta no Visual Studio. Este passo a passo mostra como integrar informações sobre a janela da ferramenta em uma nova página **de Opções** e uma nova configuração na página **Propriedades,** e também como escrever nas janelas **Lista de tarefas** e **saída.**

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Crie uma extensão com uma janela de ferramenta

1. Crie um projeto chamado **TodoList** usando o modelo VSIX e adicione um modelo personalizado de item de janela de ferramenta chamado **TodoWindow**.

    > [!NOTE]
    > Para obter mais informações sobre como criar uma extensão com uma janela de ferramenta, consulte [Criar uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Configure a janela da ferramenta
 Adicione uma TextBox para digitar um novo item ToDo, um botão para adicionar o novo item à lista e uma ListBox para exibir os itens da lista.

1. Em *TodoWindow.xaml,* exclua os controles Button, TextBox e StackPanel do UserControl.

    > [!NOTE]
    > Isso não exclui o manipulador de eventos **button1_Click,** que você reutilizará posteriormente.

2. Na seção **Todos os Controles WPF** da caixa de **ferramentas,** arraste um controle **de tela** para a grade.

3. Arraste uma **TextBox,** um **botão**e uma **Caixa de Lista** para a tela. Organize os elementos para que a TextBox e o botão estejam no mesmo nível, e a ListBox preencha o resto da janela abaixo deles, como na imagem abaixo.

     ![Janela da ferramenta finalizada](../extensibility/media/t5-toolwindow.png "Janela t5-tool")

4. No painel XAML, encontre o botão e defina sua propriedade Conteúdo para **Adicionar**. Reconecte o manipulador de eventos do `Click="button1_Click"` botão ao controle button adicionando um atributo. O bloco Canvas deve ser assim:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Personalize o construtor

1. No arquivo *TodoWindowControl.xaml.cs,* adicione o seguinte usando a diretiva:

    ```csharp
    using System;
    ```

2. Adicione uma referência pública ao TodoWindow e faça com que o construtor TodoWindowControl tome um parâmetro TodoWindow. O código deve ser assim:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. Em *TodoWindow.cs,* altere o construtor TodoWindowControl para incluir o parâmetro TodoWindow. O código deve ser assim:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Crie uma página de Opções
 Você pode fornecer uma página na caixa de diálogo **Opções** para que os usuários possam alterar as configurações da janela da ferramenta. Criar uma página Opções requer uma classe que descreva as opções e uma entrada no arquivo *TodoListPackage.cs* ou *TodoListPackage.vb.*

1. Adicione uma classe chamada `ToolsOptions.cs`. Faça `ToolsOptions` a classe <xref:Microsoft.VisualStudio.Shell.DialogPage>herdar de .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Adicione o seguinte usando a orientação:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. A página Opções neste passo a passo fornece apenas uma opção chamada DaysAhead. Adicione um campo privado chamado **daysAhead** e `ToolsOptions` uma propriedade chamada **DaysAhead** à classe:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Agora você deve tornar o projeto ciente desta página Opções.

### <a name="make-the-options-page-available-to-users"></a>Disponibilize a página Opções para os usuários

1. Em *TodoWindowPackage.cs,* <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> adicione `TodoWindowPackage` a à classe:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. O primeiro parâmetro para o construtor ProvideOptionPage é `ToolsOptions`o tipo de classe, que você criou anteriormente. O segundo parâmetro, "ToDo", é o nome da categoria na caixa de diálogo **Opções.** O terceiro parâmetro, "Geral", é o nome da subcategoria da caixa de diálogo **Opções** onde a página Opções estará disponível. Os próximos dois parâmetros são IDs de recursos para strings; o primeiro é o nome da categoria, e o segundo é o nome da subcategoria. O parâmetro final determina se esta página pode ser acessada usando automação.

     Quando um usuário abre sua página Opções, ela deve se assemelhar à seguinte imagem.

     ![Página de Opções](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Observe a categoria **ToDo** e a subcategoria **Geral**.

## <a name="make-data-available-to-the-properties-window"></a>Disponibilize dados para a janela Propriedades
 Você pode disponibilizar as informações da lista `TodoItem` ToDo criando uma classe chamada que armazena informações sobre os itens individuais na lista ToDo.

1. Adicione uma classe chamada `TodoItem.cs`.

     Quando a janela da ferramenta estiver disponível para os usuários, os itens da ListBox serão representados por TodoItems. Quando o usuário selecionar um desses itens na ListBox, a janela **Propriedades** exibirá informações sobre o item.

     Para disponibilizar dados na janela **Propriedades,** você transforma os dados em `Description` propriedades `Category`públicas que possuem dois atributos especiais, e . `Description`é o texto que aparece na parte inferior da janela **Propriedades.** `Category`determina onde a propriedade deve aparecer quando a janela **Propriedades** é exibida na **exibição Categorizada.** Na imagem a seguir, a janela **Propriedades** está na exibição **categorizada,** a propriedade **Nome** na categoria **Campos ToDo** é selecionada e a descrição da propriedade **Nome** é exibida na parte inferior da janela.

     ![Janela de propriedades](../extensibility/media/t5properties.png "T5Propriedades")

2. Adicione as seguintes diretivas que o *arquivo TodoItem.cs.*

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Adicione `public` o modificador de acesso à declaração de classe.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Adicione as duas `Name` `DueDate`propriedades e . Nós vamos fazer `UpdateList()` `CheckForErrors()` o e mais tarde.

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. Adicione uma referência privada ao controle do usuário. Adicione um construtor que leve o controle do usuário e o nome deste item ToDo. Para encontrar o `daysAhead`valor, ele obtém a propriedade de página Opções.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. Como as `TodoItem` instâncias da classe serão armazenadas na ListBox e a ListBox chamará a `ToString` função, você deve sobrecarregar a `ToString` função. Adicione o seguinte código a *TodoItem.cs,* após o construtor e antes do final da aula.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. Em *TodoWindowControl.xaml.cs,* adicione métodos `TodoWindowControl` de `CheckForError` stub `UpdateList` à classe para os métodos e métodos. Coloque-os após o ProcessDialogChar e antes do final do arquivo.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     O `CheckForError` método chamará um método que tem o mesmo nome no objeto pai, e esse método verificará se houve algum erro e os manuseará corretamente. O `UpdateList` método atualizará o ListBox no controle pai; o método é `Name` chamado `DueDate` quando as propriedades nesta classe mudam. Eles serão implementados mais tarde.

## <a name="integrate-into-the-properties-window"></a>Integre-se à janela Propriedades
 Agora escreva o código que gerencia o ListBox, que será vinculado à janela **Propriedades.**

 Você deve alterar o manipulador de cliques de botão para ler a TextBox, criar um TodoItem e adiciona-o à ListBox.

1. Substitua a `button1_Click` função existente por um código que cria um novo TodoItem e adicione-o à ListBox. Ele `TrackSelection()`chama , que será definido mais tarde.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Na exibição Design, selecione o controle ListBox. Na janela **Propriedades,** clique no botão **'Manipuladores de eventos'** e encontre o evento **SelectionChanged.** Preencha a caixa de texto com **listBox_SelectionChanged**. Fazendo isso, adiciona um stub para um manipulador SelectionChanged e atribui-o ao evento.

3. Implementar o método de `TrackSelection()` . Uma vez que você <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> precisará obter os <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> serviços, você precisa tornar o acessível pelo TodoWindowControl. Adicione o seguinte método à classe `TodoWindow`:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Adicione as seguintes diretivas usando *TodoWindowControl.xaml.cs:*

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Preencha o manipulador SelectionChanged da seguinte forma:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Agora, preencha a função TrackSelection, que fornecerá integração com a janela **Propriedades.** Esta função é chamada quando o usuário adiciona um item à ListBox ou clica em um item na ListBox. Ele adiciona o conteúdo da ListBox a um SelectionContainer e passa <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> o SelectionContainer para o manipulador de eventos da janela **Propriedades.** O serviço TrackSelection rastreia objetos selecionados na interface do usuário (UI) e exibe suas propriedades

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     Agora que você tem uma classe que a janela **Propriedades** pode usar, você pode integrar a janela **Propriedades** com a janela da ferramenta. Quando o usuário clica em um item na ListBox na janela da ferramenta, a janela **Propriedades** deve ser atualizada em conformidade. Da mesma forma, quando o usuário altera um item ToDo na janela **Propriedades,** o item associado deve ser atualizado.

7. Agora, adicione o resto do código de função UpdateList em *TodoWindowControl.xaml.cs*. Ele deve soltar e adicionar o TodoItem modificado da ListBox.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Teste seu código. Compile o projeto e comece a depuração. A instância experimental deve aparecer.

9. Abra a página**Opções de** **Ferramentas.** >  Você deve ver a categoria ToDo no painel esquerdo. As categorias estão listadas em alfabética, então olhe sob os Ts.

10. Na página **Todas** as opções, você deve ver a `DaysAhead` propriedade definida como **0**. Mude para **2**.

11. No **menu Ver / Outros Windows,** abra **TodoWindow**. Digite **EndDate** na caixa de texto e clique **em Adicionar**.

12. Na caixa de lista você deve ver uma data dois dias depois do dia de hoje.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Adicione texto à janela Saída e itens à Lista de Tarefas
 Para a **lista de tarefas,** você cria um novo objeto de tarefa de `Add` tipo e, em seguida, adiciona esse objeto Tarefa à Lista de **tarefas,** chamando seu método. Para escrever na janela **Saída,** você chama seu `GetPane` método para obter `OutputString` um objeto de painel e, em seguida, você chama o método do objeto painel.

1. Em *TodoWindowControl.xaml.cs,* `button1_Click` no método, adicione código para obter o painel **Geral** da janela **Saída** (que é o padrão) e escreva para ele. O método deverá ter esta aparência:

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Para adicionar itens à Lista de Tarefas, você precisa adicionar uma classe aninhada à classe TodoWindowControl. A classe aninhada <xref:Microsoft.VisualStudio.Shell.TaskProvider>precisa derivar de . Adicione o seguinte código ao `TodoWindowControl` final da classe.

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. Em seguida, adicione `TodoTaskProvider` uma `CreateProvider()` referência `TodoWindowControl` privada e um método à classe. O código deve ser assim:

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. Adicionar `ClearError()`, o que limpa `ReportError()`a Lista de Tarefas e , `TodoWindowControl` que adiciona uma entrada à Lista de Tarefas, à classe.

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. Agora implemente o `CheckForErrors` método, da seguinte forma.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>Experimentar

1. Compile o projeto e comece a depuração. A instância experimental aparece.

2. Abra o **TodoWindow** **(Exibir** > **Outros Windows** > **TodoWindow).**

3. Digite algo na caixa de texto e clique em **Adicionar**.

     Uma data de vencimento 2 dias após hoje é adicionada à caixa de lista. Nenhum erro é gerado, e a **Lista de tarefas** **(Exibir** > **lista de**tarefas) não deve ter entradas.

4. Agora altere a configuração na página**Opções** >  **de ferramentas** > **ToDo** de **2** para **0**.

5. Digite outra coisa no **TodoWindow** e clique em **Adicionar** novamente. Isso desencadeia um erro e também uma entrada na **Lista de Tarefas**.

     À medida que você adiciona itens, a data inicial está definida para agora mais 2 dias.

6. No **menu Exibir,** clique **em Sair** para abrir a janela **Saída.**

     Observe que toda vez que você adiciona um item, uma mensagem é exibida no painel **Lista de tarefas.**

7. Clique em um dos itens na ListBox.

     A janela **Propriedades** exibe as duas propriedades para o item.

8. Altere uma das propriedades e pressione **Enter**.

     O item é atualizado na ListBox.
