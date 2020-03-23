---
title: Severidade e supressão das regras do analisador
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431404"
---
# <a name="use-code-analyzers"></a>Use analisadores de código

Os analisadores de código .NET Compiler Platform ("Roslyn") analisam seu código C# ou Visual Basic à medida que você digita. Cada *diagnóstico* ou regra tem um estado de gravidade e supressão padrão que pode ser substituído para o seu projeto. Este artigo abrange a definição da gravidade das regras, o uso de regras e a supressão de violações.

## <a name="analyzers-in-solution-explorer"></a>Analisadores no Solution Explorer

Você pode fazer grande parte da personalização dos diagnósticos do analisador do **Solution Explorer**. Se você [instalar analisadores](../code-quality/install-roslyn-analyzers.md) como um pacote NuGet, um nó **Analyzers** será exibido no nó **Referências** ou **Dependências** no **Solution Explorer**. Se você expandir **os Analisadores**e, em seguida, expandir um dos conjuntos de analisadores, verá todos os diagnósticos na montagem.

![Nó de analisadores no Solution Explorer](media/analyzers-expanded-in-solution-explorer.png)

Você pode visualizar as propriedades de um diagnóstico, incluindo sua descrição e gravidade padrão, na janela **Propriedades.** Para exibir as propriedades, clique com o botão direito do mouse na regra e selecione **Propriedades,** ou selecione a regra e pressione **Alt**+**Enter**.

![Propriedades de diagnóstico na janela Propriedades](media/analyzer-diagnostic-properties.png)

Para ver a documentação on-line para um diagnóstico, clique com o botão direito do mouse no diagnóstico e **selecione Exibir ajuda**.

Os ícones ao lado de cada diagnóstico no **Solution Explorer** correspondem aos ícones que você vê no conjunto de regras quando você o abre no editor:

- o "x" em um círculo indica uma [gravidade](#rule-severity) de **erro**
- o "!" em um triângulo indica uma [gravidade](#rule-severity) de **Aviso**
- o "i" em um círculo indica uma [gravidade da](#rule-severity) **Informação**
- o "i" em um círculo em um fundo de cor clara indica uma [gravidade](#rule-severity) de **Hidden**
- a seta apontando para baixo em um círculo indica que o diagnóstico é suprimido

![Ícones de diagnóstico no Solution Explorer](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Gravidade da regra

::: moniker range=">=vs-2019"

Você pode configurar a gravidade das regras do analisador ou *diagnóstico,* se você [instalar os analisadores](../code-quality/install-roslyn-analyzers.md) como um pacote NuGet. A partir da versão 16.3 do Visual Studio 2019, você pode configurar a gravidade de uma regra [em um arquivo EditorConfig](#set-rule-severity-in-an-editorconfig-file). Você também pode alterar a gravidade de uma regra [do Solution Explorer](#set-rule-severity-from-solution-explorer) ou em um arquivo definido por [regras](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Você pode configurar a gravidade das regras do analisador ou *diagnóstico,* se você [instalar os analisadores](../code-quality/install-roslyn-analyzers.md) como um pacote NuGet. Você pode alterar a gravidade de uma regra [do Solution Explorer](#set-rule-severity-from-solution-explorer) ou em um arquivo definido por [regras](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

A tabela a seguir mostra as diferentes opções de gravidade:

| Gravidade (Explorador de Soluções) | Gravidade (arquivo EditorConfig) | Comportamento de tempo de construção | Comportamento do editor |
|-|-|-|
| Erro | `error` | As violações aparecem como *erros* na lista de erros e na saída de compilação de linha de comando e fazem com que as compilações falhem.| O código ofensivo é sublinhado com um rabisco vermelho e marcado por uma pequena caixa vermelha na barra de rolagem. |
| Aviso | `warning` | As violações aparecem como *Avisos* na Lista de erros e na saída de compilação de linha de comando, mas não causam falhas nas compilações. | O código ofensivo é sublinhado com um rabisco verde e marcado por uma pequena caixa verde na barra de rolagem. |
| Informações | `suggestion` | As violações aparecem como *Mensagens* na Lista de erros e não na saída de compilação de linha de comando. | O código ofensivo é sublinhado com um rabisco cinza e marcado por uma pequena caixa cinza na barra de rolagem. |
| Hidden | `silent` | Não visível para o usuário. | Não visível para o usuário. No entanto, o diagnóstico é relatado ao motor de diagnóstico do IDE. |
| Nenhum | `none` | Suprimido completamente. | Suprimido completamente. |
| Padrão | `default` | Corresponde à gravidade padrão da regra. Para determinar qual é o valor padrão de uma regra, procure na janela Propriedades. | Corresponde à gravidade padrão da regra. |

A captura de tela a seguir do editor de código mostra três violações diferentes com diferentes gravidades. Observe a cor do squiggle e o quadrado pequeno e colorido na barra de rolagem à direita.

![Erro, aviso e violação de informações no editor de código](media/diagnostics-severity-colors.png)

A captura de tela a seguir mostra as mesmas três violações que aparecem na Lista de erros:

![Erro, aviso e violação de informações na Lista de Erros](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Defina a gravidade das regras em um arquivo EditorConfig

(Visual Studio 2019 versão 16.3 e posterior)

Você pode definir a gravidade para avisos de compilador ou regras de analisador em um arquivo EditorConfig com a seguinte sintaxe:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Definir a gravidade de uma regra em um arquivo EditorConfig tem precedência sobre qualquer gravidade definida em um conjunto de regras ou no Solution Explorer. Você pode configurar [manualmente](#manually-configure-rule-severity) a gravidade em um arquivo EditorConfig ou [automaticamente](#automatically-configure-rule-severity) através da lâmpada que aparece ao lado de uma violação.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Defina a gravidade das regras de vários analisadores de uma só vez em um arquivo EditorConfig

(Visual Studio 2019 versão 16.5 e posterior)

Você pode definir a gravidade para uma categoria específica de regras de analisador ou para todas as regras do analisador com uma única entrada em um arquivo EditorConfig.

- Defina a gravidade das regras para uma categoria de regras do analisador:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Defina a gravidade das regras para todas as regras do analisador:

`dotnet_analyzer_diagnostic.severity = <severity>`

Se você tiver várias entradas aplicáveis a um ID de regra específica, a seguinte é a ordem de precedência para escolher a entrada aplicável:

- A entrada de gravidade para uma regra individual por ID tem precedência sobre a entrada de gravidade para uma categoria.
- A entrada de gravidade para uma categoria tem precedência sobre a entrada de gravidade para todas as regras do analisador.

Considere o seguinte exemplo do EditorConfig, onde [ca1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) tem a categoria "Desempenho":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

No exemplo anterior, todas as três entradas são aplicáveis ao CA1822. No entanto, usando as regras de precedência especificadas, a primeira entrada de gravidade baseada em ID de regra ganha sobre as próximas entradas. Neste exemplo, o CA1822 terá uma gravidade efetiva de "erro". Todas as demais regras com a categoria "Desempenho" terão gravidade "aviso". Todas as demais regras do analisador, que não possuem a categoria "Desempenho", terão severidade de "sugestão".

#### <a name="manually-configure-rule-severity"></a>Configurar manualmente a gravidade das regras

1. Se você ainda não tiver um arquivo EditorConfig para o seu projeto, [adicione um](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Adicione uma entrada para cada regra que deseja configurar a extensão de arquivo correspondente. Por exemplo, para definir a gravidade de [CA1822](ca1822.md) para `error` arquivos C#, a entrada parece a seguinte:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Para analisadores de estilo de código IDE, você também pode configurá-los em um `dotnet_style_qualification_for_field = false:suggestion`arquivo EditorConfig usando uma sintaxe diferente, por exemplo, . No entanto, se você definir `dotnet_diagnostic` uma gravidade usando a sintaxe, ela tem precedência. Para obter mais informações, consulte [convenções de idiomas para EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Converta um arquivo Ruleset existente no arquivo EditorConfig

A partir da versão 16.5 do Visual Studio 2019, os arquivos ruleset são preteridos em favor do arquivo EditorConfig para configuração do analisador para código gerenciado. A maioria das ferramentas do Visual Studio para a configuração de gravidade da regra do analisador foi atualizada para funcionar em arquivos do EditorConfig em vez de arquivos definidos por regras. Os arquivos EditorConfig permitem configurar as formas de regra do analisador e as opções de analisador, incluindo opções de estilo de código Visual Studio IDE. É altamente recomendável que você converta seu arquivo de regras existente em um arquivo EditorConfig. Também é recomendável que você salve o arquivo EditorConfig na raiz do seu repo ou na pasta de solução. Usando a raiz de sua pasta de relo ou solução, certifique-se de que as configurações de gravidade deste arquivo sejam automaticamente aplicadas a todo o repo ou solução, respectivamente.

Existem algumas maneiras de converter um arquivo de regras existente em um arquivo EditorConfig:

- Do Editor Ruleset no Visual Studio (requer visual studio 2019 16.5 ou posterior). Se o seu projeto já usar `CodeAnalysisRuleSet`um arquivo definido de regras específica como seu, você pode convertê-lo em um arquivo EditorConfig equivalente do Editor Ruleset dentro do Visual Studio.

    1. Clique duas vezes no arquivo de configuração de regras no Solution Explorer.

       O arquivo Ruleset deve ser aberto no Editor Ruleset. Você deve ver uma **barra de informações** clicável na parte superior do editor do conjunto de regras.

       ![Converter configuração de regras para o arquivo EditorConfig no Editor Ruleset](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Clique** no link infobar.

       Isso deve abrir uma caixa de diálogo **Salvar como** que permite selecionar o diretório onde deseja gerar o arquivo EditorConfig.

    3. **Clique** no botão **Salvar** para gerar o arquivo EditorConfig.

       O EditorConfig gerado deve abrir no editor. Além disso, a propriedade `CodeAnalysisRuleSet` MSBuild é atualizada no arquivo do projeto para que ele não faça mais referência ao arquivo conjunto de regras original.

- Na linha de comando:

    1. Instale o pacote NuGet [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Execute `RulesetToEditorconfigConverter.exe` a partir do pacote instalado, com caminhos para o arquivo ruleset e o arquivo EditorConfig como argumentos de linha de comando.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Aqui está um exemplo de arquivo definido por regras para converter:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

Aqui está o arquivo EditorConfig convertido:

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```

#### <a name="automatically-configure-rule-severity"></a>Configure automaticamente a gravidade das regras

##### <a name="configure-from-light-bulb-menu"></a>Configurar a partir do menu da lâmpada

O Visual Studio fornece uma maneira conveniente de configurar a gravidade de uma regra a partir do menu de [lâmpadas Quick Actions.](../ide/quick-actions.md)

1. Após uma violação, paire sobre a violação no editor e abra o menu da lâmpada. Ou, coloque o cursor na linha e pressione **Ctrl**+**.** (ponto).

2. No menu da lâmpada, selecione **Configurar ou Suprimir problemas** > **Configure \<a severidade de ida> de regra**.

   ![Configure a gravidade das regras do menu de lâmpadas no Visual Studio](media/configure-rule-severity.png)

3. A partir daí, selecione uma das opções de gravidade.

   ![Configure a gravidade das regras como Sugestão](media/configure-rule-severity-suggestion.png)

   O Visual Studio adiciona uma entrada ao arquivo EditorConfig para configurar a regra ao nível solicitado, conforme mostrado na caixa de visualização.

   > [!TIP]
   > Se você ainda não tiver um arquivo EditorConfig no projeto, o Visual Studio criará um para você.

##### <a name="configure-from-error-list"></a>Configurar a partir da lista de erros

O Visual Studio também fornece uma maneira conveniente de configurar a gravidade de uma regra a partir do menu de contexto da lista de erros.

1. Após uma violação ocorrer, clique com o botão direito do mouse na entrada de diagnóstico na lista de erros.

2. No menu de contexto, **selecione Definir gravidade**.

   ![Configure a gravidade da regra da lista de erros no Visual Studio](media/configure-rule-severity-error-list.png)

3. A partir daí, selecione uma das opções de gravidade.

   O Visual Studio adiciona uma entrada ao arquivo EditorConfig para configurar a regra no nível solicitado.

   > [!TIP]
   > Se você ainda não tiver um arquivo EditorConfig no projeto, o Visual Studio criará um para você.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Defina a gravidade das regras do Solution Explorer

1. No Solution Explorer, expanda**os Analisadores de** **Referências** > (ou**Analisadores de** **Dependências** > para projetos .NET Core).

2. Expanda a montagem que contém a regra para a que você deseja definir severidade.

::: moniker range=">=vs-2019"
3. Clique com o botão direito do mouse na regra e **selecione Definir gravidade**. No menu de contexto, selecione uma das opções de gravidade.

   O Visual Studio adiciona uma entrada ao arquivo EditorConfig para configurar a regra no nível solicitado. Se o projeto usar um arquivo definido em vez de um arquivo EditorConfig, a entrada de gravidade será adicionada ao arquivo definido por regras.

   > [!TIP]
   > Se você ainda não tiver um arquivo EditorConfig ou um arquivo definido de regras no projeto, o Visual Studio criará um novo arquivo EditorConfig para você.
::: moniker-end

::: moniker range="vs-2017"
3. Clique com o botão direito do mouse na regra e **selecione Definir gravidade de conjunto de regras**. No menu de contexto, selecione uma das opções de gravidade.

   A gravidade da regra é salva no arquivo conjunto de regras ativa.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Defina a gravidade das regras no arquivo definido por regras

![Arquivo definido de regras no Solution Explorer](media/ruleset-in-solution-explorer.png)

1. Abra o arquivo de configuração de regra ativa clicando duas vezes no **Solution Explorer,** selecionando **Open Active Rule Set** no menu com o botão direito do clique no nó**Dode do Analisador de** **Referências** > ou selecionando **Abrir** na página de propriedade De análise de **código** para o projeto.

   Se esta for a primeira vez que você estiver editando o conjunto de regras, o Visual Studio fizer uma cópia do arquivo definido de regras padrão, nomeá-lo * \<>.ruleset*e o adicionar ao seu projeto. Este conjunto de regras personalizadas também se torna o conjunto de regras ativos para o seu projeto.

   > [!NOTE]
   > Os projetos .NET Core e .NET Standard não suportam os comandos de menu para conjuntos de regras no **Solution Explorer,** por exemplo, **Open Active Rule Set**. Para especificar uma regra não padrão definida para um projeto .NET Core ou .NET Standard, adicione manualmente [a propriedade **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) ao arquivo do projeto. Você ainda pode configurar as regras dentro da regra definida no editor de regras do Visual Studio.

1. Navegue pela regra expandindo sua montagem contendo.

1. Na coluna **Ação,** selecione o valor para abrir uma lista de parada e selecione a gravidade desejada na lista.

   ![Arquivo definido de regra aberto no editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir violações

Existem várias maneiras de suprimir violações de regras:

::: moniker range=">=vs-2019"

- Em um **arquivo EditorConfig**

  Defina a gravidade `none`para, `dotnet_diagnostic.CA1822.severity = none`por exemplo, .

- Do menu **Analisar**

  Selecione **Analisar** > **criar e suprimir problemas ativos** na barra de menu para suprimir todas as violações atuais. Isso às vezes é chamado de "baseamento".

::: moniker-end

::: moniker range="vs-2017"

- Do menu **Analisar**

  Selecione **Analisar** > **a análise de código de execução e suprimir problemas ativos** na barra de menu para suprimir todas as violações atuais. Isso às vezes é chamado de "baseamento".

::: moniker-end

- Do **Solution Explorer**

  Defina a gravidade da regra para **Nenhum.**

- A partir do **editor de conjunto de regras**

  Desmarcar a caixa ao lado do nome ou definir **Ação** para **Nenhum**.

- Do **editor de código**

  Coloque o cursor na linha de código com a violação e pressione O Período **Ctrl**+**(.)** para abrir o menu **Ações Rápidas.** Selecione **Suprimir CAXXXX** > **no Arquivo de Origem/In Supressão**.

  ![Suprimir o diagnóstico do menu de ações rápidas](media/suppress-diagnostic-from-editor.png)

- Da **lista de erros**

  Selecione as regras que deseja suprimir e clique com o botão direito do mouse e **selecione Supressão** > **no Arquivo de Origem/Supressão**.

  - Se você suprimir **Em Origem,** a **caixa de diálogo 'Alterações de visualização'** será aberta e mostrará uma visualização do aviso de [#Disable c# #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) ou visual basic [#Disable](/dotnet/visual-basic/language-reference/directives/directives) que é adicionada ao código-fonte.

    ![Visualização de adicionar #pragma aviso no arquivo de código](media/pragma-warning-preview.png)

  - Se você selecionar **Em Arquivo de Supressão,** a <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> caixa de diálogo **'Visualizar's changes's** changes's changes 'supupis's to the global suppressions file's.

    ![Visualização da adição do atributo SuppressMessage ao arquivo de supressão](media/preview-changes-in-suppression-file.png)

  Na **caixa de diálogo 'Inversaver',** **'''''Inversia''**

  > [!NOTE]
  > Se você não ver a opção **Dessuprimir** menu no **Solution Explorer,** a violação provavelmente virá da compilação e não da análise ao vivo. A **Lista de Erros** exibe diagnósticos, ou violações de regras, tanto da análise de código susceptío e da compilação. Uma vez que os diagnósticos de compilação podem ser obsoletos, por exemplo, se você editou o código para corrigir a violação, mas não reconstruiu, você não pode suprimir esses diagnósticos da Lista de **erros**. Os diagnósticos da análise ao vivo, ou IntelliSense, estão sempre atualizados com as fontes atuais e podem ser suprimidos da **Lista de Erros**. Para excluir os diagnósticos de *compilação* da sua seleção, alterne o filtro de origem da **lista** de erros do **Build + IntelliSense** para **o somente IntelliSense**. Em seguida, selecione os diagnósticos que deseja suprimir e prossiga como descrito anteriormente.
  >
  > ![Filtro de origem da lista de erros no Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Uso da linha de comando

Quando você constrói seu projeto na linha de comando, as violações de regras aparecerão na saída de compilação se as seguintes condições forem atendidas:

- Os analisadores são instalados como um pacote NuGet e não como uma extensão VSIX.

- Uma ou mais regras são violadas no código do projeto.

- A [gravidade](#rule-severity) de uma regra violada é definida como **advertência**, nesse caso, as violações não causam falha na construção, ou **erro,** nesse caso as violações causam falha na construção.

A verbosidade da saída de compilação não afeta se as violações de regras são mostradas. Mesmo com verbosidade **silenciosa,** violações de regras aparecem na saída de compilação.

> [!TIP]
> Se você está acostumado a executar a análise de legado da linha de comando, seja com *fxCopCmd.exe* ou através de msbuild com o sinalizador **RunCodeAnalysis,** veja como fazer isso com analisadores de código.

Para ver violações do analisador na linha de comando ao construir seu projeto usando msbuild, execute um comando como este:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

A imagem a seguir mostra a saída de compilação de linha de comando a partir da construção de um projeto que contém uma violação de regra do analisador:

![Saída do MSBuild com violação de regra](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Projetos dependentes

Em um projeto .NET Core, se você adicionar uma referência a um projeto que tenha analisadores NuGet, esses analisadores também serão adicionados automaticamente ao projeto dependente. Para desativar esse comportamento, por exemplo, se o projeto dependente for um projeto de teste de unidade, marque o pacote NuGet como privado no arquivo *.csproj* ou *.vbproj* do projeto referenciado definindo o atributo **PrivateAssets:**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Confira também

- [Visão geral dos analisadores de código no Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar um bug do analisador de código](https://github.com/dotnet/roslyn-analyzers/issues)
- [Use conjuntos de regras](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir avisos de análise de código](../code-quality/in-source-suppression-overview.md)
