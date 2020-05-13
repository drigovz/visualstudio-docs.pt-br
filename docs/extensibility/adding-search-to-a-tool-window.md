---
title: Adicionando pesquisa a uma janela de ferramentas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740141"
---
# <a name="add-search-to-a-tool-window"></a>Adicionar pesquisa a uma janela de ferramenta
Quando você cria ou atualiza uma janela de ferramenta em sua extensão, você pode adicionar a mesma funcionalidade de pesquisa que aparece em outro lugar no Visual Studio. Essa funcionalidade inclui os seguintes recursos:

- Uma caixa de pesquisa que está sempre localizada em uma área personalizada da barra de ferramentas.

- Um indicador de progresso que está sobreposto na própria caixa de pesquisa.

- A capacidade de mostrar resultados assim que você inserir cada caractere (pesquisa instantânea) ou somente depois de escolher a chave **Enter** (pesquisa sob demanda).

- Uma lista que mostra termos para os quais você pesquisou mais recentemente.

- A capacidade de filtrar pesquisas por campos ou aspectos específicos dos alvos de pesquisa.

Seguindo este passo a passo, você aprenderá a executar as seguintes tarefas:

1. Crie um projeto VSPackage.

2. Crie uma janela de ferramenta que contenha um UserControl com uma TextBox somente lida.

3. Adicione uma caixa de pesquisa à janela da ferramenta.

4. Adicione a implementação da pesquisa.

5. Habilite a pesquisa instantânea e a exibição de uma barra de progresso.

6. Adicione uma opção **de caixa de correspondência.**

7. Adicione um **filtro de linha de pesquisa uniforme.**

## <a name="to-create-a-vsix-project"></a>Para criar um projeto VSIX

1. Crie um projeto `TestToolWindowSearch` VSIX nomeado com uma janela de ferramenta chamada **TestSearch**. Se você precisar de ajuda para fazer isso, consulte [Criando uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Para criar uma janela de ferramenta

1. No `TestToolWindowSearch` projeto, abra o arquivo *TestSearchControl.xaml.*

2. Substitua o `<StackPanel>` bloco existente pelo bloco a seguir, que adiciona uma leitura somente <xref:System.Windows.Controls.TextBox> à <xref:System.Windows.Controls.UserControl> janela da ferramenta.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. No arquivo *TestSearchControl.xaml.cs,* adicione o seguinte usando a diretiva:

    ```csharp
    using System.Text;
    ```

4. Remova `button1_Click()` o método.

     Na classe **TestSearchControl,** adicione o seguinte código.

     Esse código adiciona <xref:System.Windows.Controls.TextBox> uma propriedade pública chamada **SearchResultsTextBox** e uma propriedade de string pública chamada **SearchContent**. No construtor, searchResultsTextBox é definido na caixa de texto e o SearchContent é inicializado para um conjunto de strings delimitado por linha nova. O conteúdo da caixa de texto também é inicializado para o conjunto de strings.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Compile o projeto e comece a depuração. A instância experimental do Visual Studio aparece.

6. Na barra de menus, escolha **Exibir** > Outros Testes do**WindowsSearch** > **TestSearch**.

     A janela da ferramenta aparece, mas o controle de pesquisa ainda não aparece.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Para adicionar uma caixa de pesquisa à janela da ferramenta

1. No arquivo *TestSearch.cs,* adicione o `TestSearch` seguinte código à classe. O código substitui <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> a propriedade para que `true`o acessório obtenha retorna .

     Para habilitar a pesquisa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> você deve substituir a propriedade. A <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> implementa e fornece uma implementação padrão que não habilita a pesquisa.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Compile o projeto e comece a depuração. A instância experimental aparece.

3. Na instância experimental do Visual Studio, abra **testsearch**.

     Na parte superior da janela da ferramenta, um controle de pesquisa aparece com uma marca d'água **de pesquisa** e um ícone de lupa. No entanto, a pesquisa ainda não funciona porque o processo de pesquisa não foi implementado.

## <a name="to-add-the-search-implementation"></a>Para adicionar a implementação da pesquisa
 Quando você habilita <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>a pesquisa em um , como no procedimento anterior, a janela da ferramenta cria um host de pesquisa. Esse host configura e gerencia processos de pesquisa, que sempre ocorrem em um segmento de fundo. Como <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> a classe gerencia a criação do host de pesquisa e a configuração da pesquisa, você só precisa criar uma tarefa de pesquisa e fornecer o método de pesquisa. O processo de pesquisa ocorre em um segmento de fundo e as chamadas para o controle da janela da ferramenta ocorrem no segmento de ida e rei. Portanto, você deve usar o método [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) para gerenciar quaisquer chamadas que você fizer ao lidar com o controle.

1. No arquivo *TestSearch.cs,* adicione `using` as seguintes diretivas:

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

2. Na `TestSearch` classe, adicione o seguinte código, que executa as seguintes ações:

    - Substitui o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> método para criar uma tarefa de pesquisa.

    - Substitui o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> método para restaurar o estado da caixa de texto. Esse método é chamado quando um usuário cancela uma tarefa de pesquisa e quando um usuário define ou desconfigura opções ou filtros. Ambos <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> são chamados no segmento de ida e volta. Portanto, você não precisa acessar a caixa de texto por meio do método [ThreadHelper.Invoke*.](https://msdn.microsoft.com/data/ee197798(v=vs.85))

    - Cria uma classe nomeada `TestSearchTask` que herda de <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, que <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>fornece uma implementação padrão de .

         Em `TestSearchTask`, o construtor define um campo privado que faz referência à janela da ferramenta. Para fornecer o método de <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> pesquisa, você anula os métodos. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> O <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> método é onde você implementa o processo de pesquisa. Esse processo inclui a realização da pesquisa, a exibição dos resultados da pesquisa na caixa de texto e a chamada de implementação da classe base deste método para informar que a pesquisa está concluída.

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

    1. Reconstrua o projeto e comece a depurar.

    2. Na instância experimental do Visual Studio, abra a janela da ferramenta novamente, insira algum texto de pesquisa na janela de pesquisa e clique em **ENTER**.

         Os resultados corretos devem aparecer.

## <a name="to-customize-the-search-behavior"></a>Para personalizar o comportamento de pesquisa
 Alterando as configurações de pesquisa, você pode fazer uma variedade de alterações na forma como o controle de pesquisa aparece e como a pesquisa é realizada. Por exemplo, você pode alterar a marca d'água (o texto padrão que aparece na caixa de pesquisa), a largura mínima e máxima do controle de pesquisa e se deve mostrar uma barra de progresso. Você também pode alterar o ponto em que os resultados da pesquisa começam a aparecer (sob demanda ou pesquisa instantânea) e se deve mostrar uma lista de termos para os quais você pesquisou recentemente. Você pode encontrar a lista completa <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> de configurações da classe.

1. No arquivo* TestSearch.cs*, adicione o `TestSearch` seguinte código à classe. Esse código permite a pesquisa instantânea em vez de uma pesquisa sob demanda (o que significa que o usuário não precisa clicar em **ENTER**). O código substitui `ProvideSearchSettings` o `TestSearch` método na classe, que é necessário para alterar as configurações padrão.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Teste a nova configuração reconstruindo a solução e reiniciando o depurador.

     Os resultados da pesquisa aparecem sempre que você digita um caractere na caixa de pesquisa.

3. No `ProvideSearchSettings` método, adicione a seguinte linha, que permite a exibição de uma barra de progresso.

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

     Para que a barra de progresso apareça, o progresso deve ser relatado. Para relatar o progresso, não comente o seguinte código no `OnStartSearch` método da `TestSearchTask` classe:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Para retardar o processamento o suficiente para que a barra `OnStartSearch` de `TestSearchTask` progresso seja visível, não comente a seguinte linha no método da classe:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Teste as novas configurações reconstruindo a solução e começando a depurar.

     A barra de progresso aparece na janela de pesquisa (como uma linha azul abaixo da caixa de texto de pesquisa) toda vez que você realiza uma pesquisa.

## <a name="to-enable-users-to-refine-their-searches"></a>Para permitir que os usuários refinem suas pesquisas
 Você pode permitir que os usuários refinem suas pesquisas por meio de opções como **caso match** ou match **whole word**. As opções podem ser booleanas, que aparecem como caixas de seleção, ou comandos, que aparecem como botões. Para este passo a passo, você criará uma opção booleana.

1. No arquivo *TestSearch.cs,* adicione o `TestSearch` seguinte código à classe. O código substitui `SearchOptionsEnum` o método, que permite que a implementação da pesquisa detecte se uma determinada opção está on ou off. O código `SearchOptionsEnum` adiciona uma opção para <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> combinar caso com um enumerador. A opção de igualar o case `MatchCaseOption` também é disponibilizada como propriedade.

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

2. Na `TestSearchTask` classe, não comente a `OnStartSearch` seguinte linha no método:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Teste a opção:

    1. Compile o projeto e comece a depuração. A instância experimental aparece.

    2. Na janela da ferramenta, escolha a seta Para baixo no lado direito da caixa de texto.

         A caixa de seleção **do caso Match** é exibida.

    3. Selecione a caixa de seleção **de caixa de** seleção de correspondência e, em seguida, execute algumas pesquisas.

## <a name="to-add-a-search-filter"></a>Para adicionar um filtro de pesquisa
 Você pode adicionar filtros de pesquisa que permitem aos usuários refinar o conjunto de metas de pesquisa. Por exemplo, você pode filtrar arquivos no File Explorer pelas datas em que foram modificados mais recentemente e suas extensões de nome de arquivo. Neste passo a passo, você adicionará um filtro apenas para linhas uniformes. Quando o usuário escolhe esse filtro, o host de pesquisa adiciona as strings especificadas à consulta de pesquisa. Em seguida, você pode identificar essas strings dentro do seu método de pesquisa e filtrar os alvos de pesquisa de acordo.

1. No arquivo *TestSearch.cs,* adicione o `TestSearch` seguinte código à classe. O código `SearchFiltersEnum` implementa <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> adicionando um que especifica para filtrar os resultados de pesquisa para que apenas linhas iguais apareçam.

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

     Agora, o controle de `Search even lines only`pesquisa exibe o filtro de pesquisa . Quando o usuário escolhe o `lines:"even"` filtro, a seqüência aparece na caixa de pesquisa. Outros critérios de pesquisa podem aparecer ao mesmo tempo que o filtro. As seqüências de pesquisa podem aparecer antes do filtro, depois do filtro ou ambos.

2. No arquivo *TestSearch.cs,* adicione os seguintes métodos `TestSearchTask` à `TestSearch` classe, que está na classe. Esses métodos `OnStartSearch` suportam o método, que você modificará na próxima etapa.

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

3. Na `TestSearchTask` classe, atualize o `OnStartSearch` método com o seguinte código. Esta alteração atualiza o código para suportar o filtro.

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

5. Compile o projeto e comece a depuração. No caso experimental do Visual Studio, abra a janela da ferramenta e escolha a seta Para baixo no controle de pesquisa.

     A caixa de seleção **de caixa de** correspondência e o filtro **'Buscar' somente** linhas aparecem.

6. Escolha o filtro.

     A caixa de pesquisa contém **linhas:"even"** e os seguintes resultados aparecem:

     2 bom

     4 Bom

     6 Adeus

7. Exclua `lines:"even"` na caixa de pesquisa, selecione a `g` caixa de seleção de caixa de seleção de caixa **de** correspondência e, em seguida, digite na caixa de pesquisa.

     Os seguintes resultados aparecem:

     1 ir

     2 bom

     5 adeus

8. Escolha o X no lado direito da caixa de pesquisa.

     A busca é limpa e o conteúdo original aparece. No entanto, a caixa de seleção **de caixa de** seleção match ainda está selecionada.
