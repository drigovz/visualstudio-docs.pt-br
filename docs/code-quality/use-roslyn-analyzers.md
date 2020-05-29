---
title: Gravidade e supressão da regra do analisador
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
ms.openlocfilehash: 7e7349717478f18b676b74908da8fb8a6a2fc413
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184582"
---
# <a name="use-code-analyzers"></a>Usar analisadores de código

.NET Compiler Platform ("Roslyn") analisadores de código analisam seu código C# ou Visual Basic à medida que você digita. Cada *diagnóstico* ou regra tem um estado de gravidade e supressão padrão que pode ser substituído para seu projeto. Este artigo aborda a definição da severidade da regra, o uso de conjuntos de regras e a supressão de violações.

## <a name="analyzers-in-solution-explorer"></a>Analisadores no Gerenciador de Soluções

Você pode fazer grande parte da personalização do diagnóstico do Analyzer do **Gerenciador de soluções**. Se você [instalar os analisadores](../code-quality/install-roslyn-analyzers.md) como um pacote NuGet, um nó **analisadores** será exibido no nó **referências** ou **dependências** em **Gerenciador de soluções**. Se você expandir os **analisadores**e, em seguida, expandir um dos assemblies do analisador, verá todos os diagnósticos no assembly.

![Nó de analisadores no Gerenciador de Soluções](media/analyzers-expanded-in-solution-explorer.png)

Você pode exibir as propriedades de um diagnóstico, incluindo sua descrição e severidade padrão, na janela **Propriedades** . Para exibir as propriedades, clique com o botão direito do mouse na regra e selecione **Propriedades**, ou selecione a regra e pressione **ALT** + **Enter**.

![Propriedades de diagnóstico no janela Propriedades](media/analyzer-diagnostic-properties.png)

Para ver a documentação online de um diagnóstico, clique com o botão direito do mouse no diagnóstico e selecione **Exibir ajuda**.

Os ícones ao lado de cada diagnóstico no **Gerenciador de soluções** correspondem aos ícones que você vê no conjunto de regras ao abri-lo no editor:

- o "x" em um círculo indica uma [severidade](#rule-severity) de **erro**
- o "!" em um triângulo indica uma [severidade](#rule-severity) de **aviso**
- o "i" em um círculo indica uma [severidade](#rule-severity) de **informações**
- o "i" em um círculo em um plano de fundo com cor clara indica uma [severidade](#rule-severity) de **oculto**
- a seta apontando para baixo em um círculo indica que o diagnóstico foi suprimido

![Ícones de diagnóstico no Gerenciador de Soluções](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Gravidade da regra

::: moniker range=">=vs-2019"

Você pode configurar a severidade de regras do analisador ou *diagnóstico*, se [instalar os analisadores](../code-quality/install-roslyn-analyzers.md) como um pacote NuGet. A partir do Visual Studio 2019 versão 16,3, você pode configurar a severidade de uma regra [em um arquivo EditorConfig](#set-rule-severity-in-an-editorconfig-file). Você também pode alterar a severidade de uma regra [de Gerenciador de soluções](#set-rule-severity-from-solution-explorer) ou [em um arquivo de conjunto de regras](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Você pode configurar a severidade de regras do analisador ou *diagnóstico*, se [instalar os analisadores](../code-quality/install-roslyn-analyzers.md) como um pacote NuGet. Você pode alterar a severidade de uma regra [de Gerenciador de soluções](#set-rule-severity-from-solution-explorer) ou [em um arquivo de conjunto de regras](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

A tabela a seguir mostra as diferentes opções de gravidade:

| Gravidade (Gerenciador de Soluções) | Severidade (arquivo EditorConfig) | Comportamento de tempo de compilação | Comportamento do editor |
|-|-|-|
| Erro | `error` | As violações aparecem como *erros* na lista de erros e na saída da compilação da linha de comando e causam a falha das compilações.| O código incorreto é sublinhado com um ondulado vermelho e marcado por uma pequena caixa vermelha na barra de rolagem. |
| Aviso | `warning` | As violações aparecem como *avisos* no lista de erros e na saída da compilação da linha de comando, mas não causam a falha das compilações. | O código incorreto é sublinhado com um ondulado verde e marcado por uma pequena caixa verde na barra de rolagem. |
| Informações | `suggestion` | As violações aparecem como *mensagens* no lista de erros, e não em uma saída de compilação de linha de comando. | O código incorreto é sublinhado com um rabisco cinza e marcado por uma pequena caixa cinza na barra de rolagem. |
| Hidden | `silent` | Não visível para o usuário. | Não visível para o usuário. No entanto, o diagnóstico é reportado para o mecanismo de diagnóstico do IDE. |
| Nenhum | `none` | Suprimido completamente. | Suprimido completamente. |
| Padrão | `default` | Corresponde à severidade padrão da regra. Para determinar qual é o valor padrão de uma regra, procure na janela Propriedades. | Corresponde à severidade padrão da regra. |

A captura de tela a seguir do editor de código mostra três violações diferentes com severidades diferentes. Observe a cor do Rabisco e o pequeno quadrado colorido na barra de rolagem à direita.

![Violação de erro, aviso e informação no editor de código](media/diagnostics-severity-colors.png)

A captura de tela a seguir mostra as mesmas três violações que aparecem no Lista de Erros:

![Violação de erro, aviso e informações no Lista de Erros](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Definir a severidade da regra em um arquivo EditorConfig

(Visual Studio 2019 versão 16,3 e posterior)

Você pode definir a severidade para avisos do compilador ou regras do analisador em um arquivo EditorConfig com a seguinte sintaxe:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Definir a severidade de uma regra em um arquivo EditorConfig tem precedência sobre qualquer severidade definida em um conjunto de regras ou em Gerenciador de Soluções. Você pode configurar [manualmente](#manually-configure-rule-severity) a gravidade em um arquivo EditorConfig ou [automaticamente](#automatically-configure-rule-severity) por meio da lâmpada que aparece ao lado de uma violação.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Definir a severidade da regra de várias regras do analisador de uma só vez em um arquivo EditorConfig

(Visual Studio 2019 versão 16,5 e posterior)

Você pode definir a severidade para uma categoria específica de regras do analisador ou para todas as regras do analisador com uma única entrada em um arquivo EditorConfig.

- Defina a severidade da regra para uma categoria de regras do analisador:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Definir severidade da regra para todas as regras do analisador:

`dotnet_analyzer_diagnostic.severity = <severity>`

Se você tiver várias entradas que são aplicáveis a uma ID de regra específica, o seguinte é a ordem de precedência para escolher a entrada aplicável:

- A entrada de severidade para uma regra individual por ID tem precedência sobre a entrada de severidade de uma categoria.
- A entrada de severidade para uma categoria tem precedência sobre a entrada de severidade para todas as regras do analisador.

Considere o seguinte exemplo de EditorConfig, em que [CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) tem a categoria "performance":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

No exemplo anterior, todas as três entradas são aplicáveis a CA1822. No entanto, usando as regras de precedência especificadas, a primeira entrada de severidade com base na ID da regra vence nas próximas entradas. Neste exemplo, o CA1822 terá uma severidade efetiva de "Error". Todas as regras restantes com a categoria "desempenho" terão a severidade "aviso". Todas as demais regras do analisador, que não têm a categoria "desempenho", terão a severidade "sugestão".

#### <a name="manually-configure-rule-severity"></a>Configurar manualmente a severidade da regra

1. Se você ainda não tiver um arquivo EditorConfig para seu projeto, [adicione um](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Adicione uma entrada para cada regra que você deseja configurar na extensão de arquivo correspondente. Por exemplo, para definir a severidade de [CA1822](ca1822.md) como `error` para arquivos C#, a entrada tem a seguinte aparência:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Para analisadores de estilo de código IDE, você também pode configurá-los em um arquivo EditorConfig usando uma sintaxe diferente, por exemplo, `dotnet_style_qualification_for_field = false:suggestion` . No entanto, se você definir uma severidade usando a `dotnet_diagnostic` sintaxe, ela terá precedência. Para obter mais informações, consulte [convenções de linguagem para EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Converter um arquivo RuleSet existente no arquivo EditorConfig

A partir do Visual Studio 2019 versão 16,5, os arquivos RuleSet são preteridos em favor do arquivo EditorConfig para a configuração do analisador para código gerenciado. A maioria das ferramentas do Visual Studio para a configuração de severidade da regra do analisador foi atualizada para funcionar em arquivos EditorConfig em vez de arquivos RuleSet. Os arquivos EditorConfig permitem que você configure ambas as opções do analisador e severidades de regra do analisador, incluindo opções de estilo de código IDE do Visual Studio. É altamente recomendável que você converta o arquivo RuleSet existente em um arquivo EditorConfig. Também é recomendável que você salve o arquivo EditorConfig na raiz do seu repositório ou na pasta da solução. Usando a raiz do seu repositório ou pasta de solução, você garante que as configurações de severidade desse arquivo sejam aplicadas automaticamente a todo o repositório ou solução, respectivamente.

Há duas maneiras de converter um arquivo RuleSet existente em um arquivo EditorConfig:

- Do editor de conjunto de regras no Visual Studio (requer o Visual Studio 2019 16,5 ou posterior). Se o seu projeto já usa um arquivo RuleSet específico como seu `CodeAnalysisRuleSet` , você pode convertê-lo em um arquivo EditorConfig equivalente do editor de RuleSet no Visual Studio.

    1. Clique duas vezes no arquivo RuleSet em Gerenciador de Soluções.

       O arquivo RuleSet deve ser aberto no editor de RuleSet. Você deverá ver uma **barra** de edição clicável na parte superior do editor de conjunto de regras.

       ![Converter RuleSet em arquivo EditorConfig no editor de RuleSet](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Clique** no link da barra de links.

       Isso deve abrir uma caixa de diálogo **salvar como** que permite selecionar o diretório onde você deseja gerar o arquivo EditorConfig.

    3. **Clique** no botão **salvar** para gerar o arquivo EditorConfig.

       O EditorConfig gerado deve ser aberto no editor. Além disso, a Propriedade MSBuild `CodeAnalysisRuleSet` é atualizada no arquivo de projeto para que ele não referencie mais o arquivo RuleSet original.

- Na linha de comando:

    1. Instale o pacote NuGet [Microsoft. CodeAnalysis. RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Execute `RulesetToEditorconfigConverter.exe` a partir do pacote instalado, com caminhos para arquivo RuleSet e arquivo EditorConfig como argumentos de linha de comando.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Aqui está um exemplo de arquivo RuleSet para converter:

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

Este é o arquivo EditorConfig convertido:

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

#### <a name="automatically-configure-rule-severity"></a>Configurar automaticamente a severidade da regra

##### <a name="configure-from-light-bulb-menu"></a>Configurar no menu de lâmpada

O Visual Studio fornece uma maneira conveniente de configurar a severidade de uma regra no menu de lâmpada de [ações rápidas](../ide/quick-actions.md) .

1. Após a ocorrência de uma violação, focalize o rabisco da violação no editor e abra o menu de lâmpada. Ou coloque o cursor na linha e pressione **Ctrl** + **.** (ponto).

2. No menu de lâmpada, selecione **Configurar ou suprimir problemas** > **Configurar \<rule ID> severidade**.

   ![Configurar a severidade da regra no menu de lâmpada no Visual Studio](media/configure-rule-severity.png)

3. A partir daí, selecione uma das opções de gravidade.

   ![Configurar a severidade da regra como sugestão](media/configure-rule-severity-suggestion.png)

   O Visual Studio adiciona uma entrada ao arquivo EditorConfig para configurar a regra para o nível solicitado, conforme mostrado na caixa de visualização.

   > [!TIP]
   > Se você ainda não tiver um arquivo EditorConfig no projeto, o Visual Studio criará um para você.

##### <a name="configure-from-error-list"></a>Configurar na lista de erros

O Visual Studio também fornece uma maneira conveniente de configurar a severidade de uma regra no menu de contexto da lista de erros.

1. Após a ocorrência de uma violação, clique com o botão direito do mouse na entrada de diagnóstico na lista de erros.

2. No menu de contexto, selecione **definir severidade**.

   ![Configurar a severidade da regra na lista de erros no Visual Studio](media/configure-rule-severity-error-list.png)

3. A partir daí, selecione uma das opções de gravidade.

   O Visual Studio adiciona uma entrada ao arquivo EditorConfig para configurar a regra para o nível solicitado.

   > [!TIP]
   > Se você ainda não tiver um arquivo EditorConfig no projeto, o Visual Studio criará um para você.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Definir a severidade da regra de Gerenciador de Soluções

1. Em Gerenciador de soluções, expanda **referências**  >  **analisadores** (ou **Dependencies**  >  **analisadores** de dependências para projetos do .NET Core).

2. Expanda o assembly que contém a regra para a qual você deseja definir a severidade.

::: moniker range=">=vs-2019"
3. Clique com o botão direito do mouse na regra e selecione **definir severidade**. No menu de contexto, selecione uma das opções de gravidade.

   O Visual Studio adiciona uma entrada ao arquivo EditorConfig para configurar a regra para o nível solicitado. Se o seu projeto usa um arquivo RuleSet em vez de um arquivo EditorConfig, a entrada de severidade é adicionada ao arquivo RuleSet.

   > [!TIP]
   > Se você ainda não tiver um arquivo EditorConfig ou um arquivo RuleSet no projeto, o Visual Studio criará um novo arquivo EditorConfig para você.
::: moniker-end

::: moniker range="vs-2017"
3. Clique com o botão direito do mouse na regra e selecione **definir severidade do conjunto de regras**. No menu de contexto, selecione uma das opções de gravidade.

   A severidade da regra é salva no arquivo de conjunto de regras ativo.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Definir a severidade da regra no arquivo de conjunto de regras

![Arquivo de conjunto de regras no Gerenciador de Soluções](media/ruleset-in-solution-explorer.png)

1. Abra o arquivo do conjunto de regras ativo clicando duas vezes nele em **Gerenciador de soluções**, selecionando **abrir conjunto de regras ativas** no menu do botão direito do mouse do **References**  >  nó**analisadores** de referências ou selecionando **abrir** na página de propriedades de **análise de código** do projeto.

   Se esta for a primeira vez que você está editando o conjunto de regras, o Visual Studio faz uma cópia do arquivo de conjunto de regras padrão, nomeia-o * \<projectname> . RuleSet*e o adiciona ao seu projeto. Esse conjunto de regras personalizadas também se torna o conjunto de regras ativo para seu projeto.

   > [!NOTE]
   > Os projetos .NET Core e .NET Standard não dão suporte aos comandos de menu para conjuntos de regras em **Gerenciador de soluções**, por exemplo, **abrir conjunto de regras ativas**. Para especificar um conjunto de regras não padrão para um projeto do .NET Core ou .NET Standard, [adicione manualmente a propriedade **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) ao arquivo do projeto. Você ainda pode configurar as regras dentro do conjunto de regras na interface do usuário do editor de conjunto de regras do Visual Studio.

1. Navegue até a regra expandindo seu assembly recipiente.

1. Na coluna **ação** , selecione o valor para abrir uma lista suspensa e selecione a severidade desejada na lista.

   ![Arquivo de conjunto de regras aberto no editor](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Configurar o código gerado

Os analisadores são executados em todos os arquivos de origem em um projeto e violações de relatório sobre eles. No entanto, essas violações não são úteis em arquivos de código gerados, como arquivos de código gerados pelo designer, arquivos de origem temporários gerados pelo sistema de compilação etc. Os usuários não podem editar esses arquivos manualmente e/ou não se preocupam com a correção de violações nesses tipos de arquivos gerados por ferramentas.

Por padrão, o driver do analisador que executa analisadores trata arquivos com determinado nome, extensão de arquivo ou cabeçalho de arquivo gerado automaticamente como arquivos de código gerados. Por exemplo, um nome de arquivo que termina com `.designer.cs` ou `.generated.cs` é considerado código gerado. No entanto, essas heurísticas podem não ser capazes de identificar todos os arquivos de código gerados personalizados no código-fonte do usuário.

A partir do Visual Studio 2019 16,5, os usuários finais podem configurar arquivos e/ou pastas específicos para serem tratados como código gerado em um [arquivo EditorConfig](https://editorconfig.org/). Siga as etapas abaixo para adicionar essa configuração:

1. Se você ainda não tiver um arquivo EditorConfig para seu projeto, [adicione um](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Adicione a `generated_code = true | false` entrada para arquivos e/ou pastas específicas. Por exemplo, para tratar todos os arquivos cujo nome termina com `.MyGenerated.cs` o código gerado, a entrada seria a seguinte:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Suprimir violações

Há várias maneiras de suprimir violações de regra:

::: moniker range=">=vs-2019"

- Em um **arquivo EditorConfig**

  Defina a severidade como `none` , por exemplo, `dotnet_diagnostic.CA1822.severity = none` .

- No menu **analisar**

  Selecione **analisar**  >  **Compilar e suprimir problemas ativos** na barra de menus para suprimir todas as violações atuais. Isso às vezes é chamado de "linha de base".

::: moniker-end

::: moniker range="vs-2017"

- No menu **analisar**

  Selecione **analisar**  >  **executar análise de código e suprimir problemas ativos** na barra de menus para suprimir todas as violações atuais. Isso às vezes é chamado de "linha de base".

::: moniker-end

- De **Gerenciador de soluções**

  Defina a severidade da regra como **nenhuma**.

- Do **Editor de conjunto de regras**

  Desmarque a caixa ao lado de seu nome ou defina a **ação** como **nenhum**.

- No **Editor de código**

  Coloque o cursor na linha de código com a violação e pressione **Ctrl** + **ponto (.)** para abrir o menu **ações rápidas** . Selecione **suprimir CAXXXX**  >  **na origem/no arquivo de supressão**.

  ![Suprimir diagnóstico do menu de ações rápidas](media/suppress-diagnostic-from-editor.png)

- Da **lista de erros**

  Selecione as regras que você deseja suprimir e clique com o botão direito do mouse e selecione **suprimir**  >  **na origem/no arquivo de supressão**.

  - Se você suprimir **na origem**, a caixa de diálogo **Visualizar alterações** será aberta e mostrará uma visualização do [aviso de #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) do C# ou Visual Basic diretiva de [aviso de #Disable](/dotnet/visual-basic/language-reference/directives/directives) que é adicionada ao código-fonte.

    ![Visualização da adição de #pragma Aviso no arquivo de código](media/pragma-warning-preview.png)

  - Se você selecionar **no arquivo de supressão**, a caixa de diálogo **Visualizar alterações** será aberta e mostrará uma visualização do <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo que é adicionado ao arquivo de supressões global.

    ![Visualização da adição do atributo SuppressMessage ao arquivo de supressão](media/preview-changes-in-suppression-file.png)

  Na caixa de diálogo **Visualizar alterações** , selecione **aplicar**.

  > [!NOTE]
  > Se você não vir a opção de menu **suprimir** em **Gerenciador de soluções**, a violação provavelmente será proveniente da compilação e não da análise dinâmica. O **lista de erros** exibe diagnósticos ou violações de regra, tanto da análise de código ao vivo quanto da compilação. Como o diagnóstico de compilação pode ser obsoleto, por exemplo, se você tiver editado o código para corrigir a violação, mas não tiver recriado, não poderá suprimir esses diagnósticos do **lista de erros**. Os diagnósticos da análise ao vivo ou do IntelliSense estão sempre atualizados com as fontes atuais e podem ser suprimidos no **lista de erros**. Para excluir o diagnóstico de *compilação* da sua seleção, alterne o filtro de origem **lista de erros** do **Build + IntelliSense** **somente para IntelliSense**. Em seguida, selecione o diagnóstico que você deseja suprimir e continue conforme descrito anteriormente.
  >
  > ![Lista de Erros filtro de origem no Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Uso da linha de comando

Quando você cria seu projeto na linha de comando, violações de regra aparecem na saída da compilação se as seguintes condições forem atendidas:

- Os analisadores são instalados como um pacote NuGet e não como uma extensão VSIX.

- Uma ou mais regras são violadas no código do projeto.

- A [severidade](#rule-severity) de uma regra violada é definida como **aviso**; nesse caso, as violações não causam a falha da compilação ou **erros**, caso em que as violações causam a falha da compilação.

O detalhamento da saída da compilação não afeta se as violações de regra são mostradas. Mesmo com detalhes **silenciosos** , violações de regra aparecem na saída da compilação.

> [!TIP]
> Se você estiver acostumado a executar a análise herdada na linha de comando, seja com *FxCopCmd. exe* ou por meio do MSBuild com o sinalizador **RunCodeAnalysis** , veja como fazer isso com analisadores de código.

Para ver as violações do analisador na linha de comando ao compilar seu projeto usando o MSBuild, execute um comando como este:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

A imagem a seguir mostra a saída da compilação de linha de comando da criação de um projeto que contém uma violação de regra do analisador:

![Saída do MSBuild com violação de regra](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Projetos dependentes

Em um projeto do .NET Core, se você adicionar uma referência a um projeto que tenha analisadores NuGet, esses analisadores serão automaticamente adicionados ao projeto dependente. Para desabilitar esse comportamento, por exemplo, se o projeto dependente for um projeto de teste de unidade, marque o pacote NuGet como privado no arquivo *. csproj* ou *. vbproj* do projeto referenciado definindo o atributo **PrivateAssets** :

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Veja também

- [Visão geral dos analisadores de código no Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar um bug do analisador de código](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usar conjuntos de regras](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir avisos de análise de código](../code-quality/in-source-suppression-overview.md)
