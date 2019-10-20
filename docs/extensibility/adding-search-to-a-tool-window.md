---
title: Adicionando pesquisa a uma janela de ferramentas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4414f6d907424a1abb56bccd1d1b125444e7c716
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648009"
---
# <a name="add-search-to-a-tool-window"></a>Adicionar pesquisa a uma janela de ferramentas
Ao criar ou atualizar uma janela de ferramentas em sua extensão, você pode adicionar a mesma funcionalidade de pesquisa que aparece em outro lugar no Visual Studio. Essa funcionalidade inclui os seguintes recursos:

- Uma caixa de pesquisa que sempre está localizada em uma área personalizada da barra de ferramentas.

- Um indicador de progresso que é sobreposto na própria caixa de pesquisa.

- A capacidade de mostrar os resultados assim que você insere cada caractere (pesquisa instantânea) ou somente depois de escolher a tecla **Enter** (Pesquisar sob demanda).

- Uma lista que mostra os termos para os quais você pesquisou mais recentemente.

- A capacidade de filtrar pesquisas por campos específicos ou aspectos dos destinos de pesquisa.

Seguindo este passo a passos, você aprenderá a executar as seguintes tarefas:

1. Crie um projeto VSPackage.

2. Crie uma janela de ferramenta que contenha um UserControl com uma caixa de texto somente leitura.

3. Adicione uma caixa de pesquisa à janela de ferramentas.

4. Adicione a implementação da pesquisa.

5. Habilite a pesquisa instantânea e a exibição de uma barra de progresso.

6. Adicione uma opção de **caso de correspondência** .

7. Adicione um filtro **apenas de linhas pares de pesquisa** .

## <a name="to-create-a-vsix-project"></a>Para criar um projeto VSIX

1. Crie um projeto VSIX chamado `TestToolWindowSearch` com uma janela de ferramentas chamada **TestSearch**. Se precisar de ajuda para fazer isso, consulte [criando uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Para criar uma janela de ferramentas

1. No `TestToolWindowSearch` projeto, abra o arquivo *TestSearchControl. XAML* .

2. Substitua o bloco de `<StackPanel>` existente pelo bloco a seguir, que adiciona uma <xref:System.Windows.Controls.TextBox> somente leitura ao <xref:System.Windows.Controls.UserControl> na janela de ferramentas.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. No arquivo *TestSearchControl.XAML.cs* , adicione a seguinte diretiva using:

    ```csharp
    using System.Text;
    ```

4. Remova o método `button1_Click()`.

     Na classe **TestSearchControl** , adicione o código a seguir.

     Esse código adiciona uma propriedade de <xref:System.Windows.Controls.TextBox> pública chamada **SearchResultsTextBox** e uma propriedade de cadeia de caracteres pública chamada **SearchContent**. No construtor, SearchResultsTextBox é definido como a caixa de texto e SearchContent é inicializado para um conjunto de cadeias de caracteres delimitados por nova linha. O conteúdo da caixa de texto também é inicializado para o conjunto de cadeias de caracteres.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Compile o projeto e comece a depuração. A instância experimental do Visual Studio é exibida.

6. Na barra de menus, escolha **exibir**  > **outras janelas** de  > **TestSearch**.

     A janela de ferramentas é exibida, mas o controle de pesquisa ainda não aparece.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Para adicionar uma caixa de pesquisa à janela de ferramentas

1. No arquivo *TestSearch.cs* , adicione o código a seguir à classe `TestSearch`. O código substitui a propriedade <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> para que o acessador get retorne `true`.

     Para habilitar a pesquisa, você deve substituir a propriedade <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>. A classe <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> e fornece uma implementação padrão que não habilita a pesquisa.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Compile o projeto e comece a depuração. A instância experimental é exibida.

3. Na instância experimental do Visual Studio, abra **TestSearch**.

     Na parte superior da janela de ferramentas, um controle de pesquisa é exibido com uma marca d' água de **pesquisa** e um ícone de lupa. No entanto, a pesquisa ainda não funciona porque o processo de pesquisa não foi implementado.

## <a name="to-add-the-search-implementation"></a>Para adicionar a implementação da pesquisa
 Quando você habilita a pesquisa em um <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, como no procedimento anterior, a janela de ferramentas cria um host de pesquisa. Esse host configura e gerencia os processos de pesquisa, que sempre ocorrem em um thread em segundo plano. Como a classe <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> gerencia a criação do host de pesquisa e a configuração da pesquisa, você só precisa criar uma tarefa de pesquisa e fornecer o método de pesquisa. O processo de pesquisa ocorre em um thread em segundo plano e as chamadas para o controle janela da ferramenta ocorrem no thread da interface do usuário. Portanto, você deve usar o método [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) para gerenciar todas as chamadas feitas para lidar com o controle.

1. No arquivo *TestSearch.cs* , adicione as seguintes diretivas de `using`:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Na classe `TestSearch`, adicione o código a seguir, que executa as seguintes ações:

    - Substitui o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> para criar uma tarefa de pesquisa.

    - Substitui o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> para restaurar o estado da caixa de texto. Esse método é chamado quando um usuário cancela uma tarefa de pesquisa e quando um usuário define ou desdefine opções ou filtros. Tanto <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> quanto <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> são chamados no thread da interface do usuário. Portanto, você não precisa acessar a caixa de texto por meio do método [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) .

    - Cria uma classe denominada `TestSearchTask` que herda de <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, que fornece uma implementação padrão de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.

         No `TestSearchTask`, o construtor define um campo privado que faz referência à janela da ferramenta. Para fornecer o método de pesquisa, você substitui os métodos <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> e <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>. O método <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> é onde você implementa o processo de pesquisa. Esse processo inclui a execução da pesquisa, a exibição dos resultados da pesquisa na caixa de texto e a chamada da implementação da classe base desse método para relatar que a pesquisa foi concluída.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. Teste sua implementação de pesquisa executando as seguintes etapas:

    1. Recompile o projeto e inicie a depuração.

    2. Na instância experimental do Visual Studio, abra a janela de ferramentas novamente, insira um texto de pesquisa na janela de pesquisa e clique em **Enter**.

         Os resultados corretos devem aparecer.

## <a name="to-customize-the-search-behavior"></a>Para personalizar o comportamento de pesquisa
 Ao alterar as configurações de pesquisa, você pode fazer uma variedade de alterações na forma como o controle de pesquisa é exibido e como a pesquisa é executada. Por exemplo, você pode alterar a marca d' água (o texto padrão que aparece na caixa de pesquisa), a largura mínima e máxima do controle de pesquisa e se deseja mostrar uma barra de progresso. Você também pode alterar o ponto em que os resultados da pesquisa começam a aparecer (sob demanda ou pesquisa instantânea) e se deseja mostrar uma lista de termos para os quais você pesquisou recentemente. Você pode encontrar a lista completa de configurações na classe <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>.

1. No arquivo * TestSearch.cs *, adicione o código a seguir à classe `TestSearch`. Esse código permite a pesquisa instantânea em vez da pesquisa sob demanda (o que significa que o usuário não precisa clicar em **Enter**). O código substitui o método `ProvideSearchSettings` na classe `TestSearch`, que é necessário para alterar as configurações padrão.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Teste a nova configuração recriando a solução e reiniciando o depurador.

     Os resultados da pesquisa aparecem toda vez que você insere um caractere na caixa de pesquisa.

3. No método `ProvideSearchSettings`, adicione a linha a seguir, que permite a exibição de uma barra de progresso.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     Para que a barra de progresso apareça, o progresso deve ser relatado. Para relatar o progresso, remova a marca de comentário do código a seguir no método `OnStartSearch` da classe `TestSearchTask`:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Para o processamento lento o suficiente para que a barra de progresso fique visível, remova a marca de comentário da linha a seguir no método `OnStartSearch` da classe `TestSearchTask`:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Teste as novas configurações recriando a solução e começando a depurar.

     A barra de progresso aparece na janela de pesquisa (como uma linha azul abaixo da caixa de texto de pesquisa) toda vez que você executa uma pesquisa.

## <a name="to-enable-users-to-refine-their-searches"></a>Para permitir que os usuários refinam suas pesquisas
 Você pode permitir que os usuários refinam suas pesquisas por meio de opções como diferenciar **maiúsculas de minúsculas** ou **Coincidir palavra inteira**. As opções podem ser booleanas, que aparecem como caixas de seleção ou comandos, que aparecem como botões. Para esta explicação, você criará uma opção booliana.

1. No arquivo *TestSearch.cs* , adicione o código a seguir à classe `TestSearch`. O código substitui o método `SearchOptionsEnum`, que permite que a implementação da pesquisa detecte se uma determinada opção está ativada ou desativada. O código no `SearchOptionsEnum` adiciona uma opção para corresponder maiúsculas e minúsculas a um enumerador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>. A opção de corresponder maiúsculas e minúsculas também é disponibilizada como a propriedade `MatchCaseOption`.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. Na classe `TestSearchTask`, remova a marca de comentário da linha a seguir no método `OnStartSearch`:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Teste a opção:

    1. Compile o projeto e comece a depuração. A instância experimental é exibida.

    2. Na janela de ferramentas, escolha a seta para baixo no lado direito da caixa de texto.

         A caixa de seleção **diferenciar maiúsculas de minúsculas** é exibida.

    3. Marque a caixa de seleção diferenciar **caso** e, em seguida, execute algumas pesquisas.

## <a name="to-add-a-search-filter"></a>Para adicionar um filtro de pesquisa
 Você pode adicionar filtros de pesquisa que permitem aos usuários refinar o conjunto de destinos de pesquisa. Por exemplo, você pode filtrar arquivos no explorador de arquivos pelas datas em que eles foram modificados mais recentemente e suas extensões de nome de arquivo. Neste tutorial, você adicionará um filtro apenas para linhas pares. Quando o usuário escolhe esse filtro, o host de pesquisa adiciona as cadeias de caracteres que você especifica à consulta de pesquisa. Em seguida, você pode identificar essas cadeias de caracteres dentro do método de pesquisa e filtrar os destinos de pesquisa de acordo.

1. No arquivo *TestSearch.cs* , adicione o código a seguir à classe `TestSearch`. O código implementa `SearchFiltersEnum` adicionando um <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> que especifica para filtrar os resultados da pesquisa para que apenas linhas iguais apareçam.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Agora, o controle de pesquisa exibe o `Search even lines only` de filtro de pesquisa. Quando o usuário escolhe o filtro, a cadeia de caracteres `lines:"even"` aparece na caixa de pesquisa. Outros critérios de pesquisa podem aparecer ao mesmo tempo que o filtro. As cadeias de caracteres de pesquisa podem aparecer antes do filtro, após o filtro, ou ambos.

2. No arquivo *TestSearch.cs* , adicione os seguintes métodos à classe `TestSearchTask`, que está na classe `TestSearch`. Esses métodos dão suporte ao método `OnStartSearch`, que você modificará na próxima etapa.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. Na classe `TestSearchTask`, atualize o método `OnStartSearch` com o código a seguir. Essa alteração atualiza o código para dar suporte ao filtro.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. Teste seu código.

5. Compile o projeto e comece a depuração. Na instância experimental do Visual Studio, abra a janela de ferramentas e escolha a seta para baixo no controle de pesquisa.

     A caixa de seleção **diferenciar caso** e o filtro **Pesquisar somente linhas** aparecerão.

6. Escolha o filtro.

     A caixa de pesquisa contém **linhas: "par"** e os seguintes resultados são exibidos:

     2 bom

     4 bom

     6 adeus

7. Exclua `lines:"even"` da caixa de pesquisa, marque a caixa de seleção diferenciar **maiúsculas de minúsculas** e, em seguida, insira `g` na caixa de pesquisa.

     Os seguintes resultados são exibidos:

     1 Go

     2 bom

     5 adeus

8. Escolha o X no lado direito da caixa de pesquisa.

     A pesquisa é desmarcada e o conteúdo original é exibido. No entanto, a caixa de seleção diferenciar **maiúsculas de minúsculas** ainda está selecionada.
