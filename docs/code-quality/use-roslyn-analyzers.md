---
title: Gravidade e supressão da regra do analisador
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6362d3f14065aaf9661e85266753642e4201ca48
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548045"
---
# <a name="use-code-analyzers"></a>Usar analisadores de código

Os analisadores de código .NET Compiler Platform ("Roslyn") C# analisam seu código ou Visual Basic à medida que você digita. Cada *diagnóstico* ou regra tem um estado de gravidade e supressão padrão que pode ser substituído para seu projeto. Este artigo aborda a definição da severidade da regra, o uso de conjuntos de regras e a supressão de violações.

## <a name="analyzers-in-solution-explorer"></a>Analisadores no Gerenciador de Soluções

Você pode fazer grande parte da personalização do diagnóstico do Analyzer do **Gerenciador de soluções**. Se você [instalar](../code-quality/install-roslyn-analyzers.md) os analisadores como um pacote NuGet, um nó analisadores será exibido no nó **referências** ou **dependências** em **Gerenciador de soluções**. Se você expandiros analisadores e, em seguida, expandir um dos assemblies do analisador, verá todos os diagnósticos no assembly.

![Nó de analisadores no Gerenciador de Soluções](media/analyzers-expanded-in-solution-explorer.png)

Você pode exibir as propriedades de um diagnóstico, incluindo sua descrição e severidade padrão, na janela **Propriedades** . Para exibir as propriedades, clique com o botão direito do mouse na regra e selecione **Propriedades**, ou selecione a regra e pressione **ALT**+**Enter**.

![Propriedades de diagnóstico no janela Propriedades](media/analyzer-diagnostic-properties.png)

Para ver a documentação online de um diagnóstico, clique com o botão direito do mouse no diagnóstico e selecione **Exibir ajuda**.

Os ícones ao lado de cada diagnóstico no **Gerenciador de soluções** correspondem aos ícones que você vê no conjunto de regras ao abri-lo no editor:

- o "i" em um círculo indica uma [severidade](#rule-severity) de **informações**
- o "!" em um triângulo indica uma [severidade](#rule-severity) de **aviso**
- o "x" em um círculo indica uma [severidade](#rule-severity) de **erro**
- o "i" em um círculo em um plano de fundo com cor clara indica uma [severidade](#rule-severity) de **oculto**
- a seta apontando para baixo em um círculo indica que o diagnóstico foi suprimido

![Ícones de diagnóstico no Gerenciador de Soluções](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Conjuntos de regras

Um [conjunto de regras](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) é um arquivo XML que armazena o estado de gravidade e supressão para diagnósticos individuais.

> [!NOTE]
> Os conjuntos de regras podem incluir regras de análise herdada e analisadores de código.

Para editar o conjunto de regras ativas no editor de conjunto de regras, clique com o botão direito do mouse no nó**analisadores** de **referências** > em **Gerenciador de soluções** e selecione **abrir conjunto de regras ativas**. Se esta for a primeira vez que você está editando o conjunto de regras, o Visual Studio fará uma cópia do arquivo de conjunto de regras padrão, nomeá-lo  *\<como ProjectName >. RuleSet*e o adicionará ao seu projeto. Esse conjunto de regras personalizadas também se torna o conjunto de regras ativo para seu projeto.

Para alterar o conjunto de regras ativo para um projeto, navegue até a guia **análise de código** das propriedades de um projeto. Selecione o conjunto de regras na lista em **executar este conjunto de regras**. Para abrir o conjunto de regras, selecione **abrir**.

> [!NOTE]
> Os projetos .NET Core e .NET Standard não dão suporte aos comandos de menu para conjuntos de regras em **Gerenciador de soluções**, por exemplo, **abrir conjunto de regras ativas**. Para especificar um conjunto de regras não padrão para um projeto do .NET Core ou .NET Standard, [adicione manualmente a propriedade **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) ao arquivo do projeto. Você ainda pode configurar as regras dentro do conjunto de regras na interface do usuário do editor de conjunto de regras do Visual Studio.

## <a name="rule-severity"></a>Gravidade da regra

Você pode configurar a severidade de regras do analisador ou *diagnóstico*, se [instalar os analisadores](../code-quality/install-roslyn-analyzers.md) como um pacote NuGet. A tabela a seguir mostra as opções de gravidade para diagnóstico:

|Severidade|Comportamento de tempo de compilação|Comportamento do editor|
|-|-|-|
|Erro|As violações aparecem como *erros* na **lista de erros** e na saída da compilação da linha de comando e causam a falha das compilações.|O código incorreto é sublinhado com um ondulado vermelho e marcado por uma pequena caixa vermelha na barra de rolagem.|
|Aviso|As violações aparecem como *avisos* no **lista de erros** e na saída da compilação da linha de comando, mas não causam a falha das compilações.|O código incorreto é sublinhado com um ondulado verde e marcado por uma pequena caixa verde na barra de rolagem.|
|Info|As violações aparecem como *mensagens* no **lista de erros**, e não em uma saída de compilação de linha de comando.|O código incorreto é sublinhado com um ondulado cinza e marcado por uma pequena caixa cinza na barra de rolagem.|
|Hidden|Não visível para o usuário.|Não visível para o usuário. No entanto, o diagnóstico é reportado para o mecanismo de diagnóstico do IDE.|
|Nenhum|Suprimido completamente.|Suprimido completamente.|

Além disso, você pode "redefinir" a severidade de uma regra definindo-a como **padrão**. Cada diagnóstico tem uma severidade padrão que pode ser vista na janela **Propriedades** .

A captura de tela a seguir mostra três violações de diagnóstico diferentes no editor de código, com três severidades diferentes. Observe a cor do rabisco, bem como a pequena caixa na barra de rolagem à direita.

![Violação de erro, aviso e informação no editor de código](media/diagnostics-severity-colors.png)

A captura de tela a seguir mostra as mesmas três violações que aparecem no **lista de erros**:

![Violação de erro, aviso e informações no Lista de Erros](media/diagnostics-severities-in-error-list.png)

Você pode alterar a severidade de uma regra de **Gerenciador de soluções**ou dentro do  *\<arquivo ProjectName >. RuleSet* que é adicionado à solução depois de alterar a severidade de uma regra no **Gerenciador de soluções**.

![Arquivo de conjunto de regras no Gerenciador de Soluções](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>Definir a severidade da regra de Gerenciador de Soluções

1. Em **Gerenciador de soluções**, expanda **referências** > **analisadores** (**analisadores** de**dependências** > para projetos do .NET Core).

1. Expanda o assembly que contém a regra para a qual você deseja definir a severidade.

1. Clique com o botão direito do mouse na regra e selecione **definir severidade do conjunto de regras**. No menu suspenso, selecione uma das opções de gravidade.

   A severidade da regra é salva no arquivo de conjunto de regras ativo.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Definir a severidade da regra no arquivo de conjunto de regras

1. Abra o arquivo do [conjunto de regras](analyzer-rule-sets.md) clicando duas vezes nele em **Gerenciador de soluções**, selecionando **abrir conjunto de regras ativas** no menu do botão direito do mouse do nó analisadores ou selecionando **abrir** na página de propriedades de **análise de código** para o projeto.

1. Navegue até a regra expandindo seu assembly recipiente.

1. Na coluna **ação** , selecione o valor para abrir uma lista suspensa e selecione a severidade desejada na lista.

   ![Arquivo de conjunto de regras aberto no editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir violações

Há várias maneiras de suprimir violações de regra:

- No menu **analisar**

  Selecione **analisar** > **executar análise de código e suprimir problemas ativos** na barra de menus para suprimir todas as violações atuais. Isso às vezes é chamado de "linha de base".

- De **Gerenciador de soluções**

  Para suprimir uma violação no **Gerenciador de soluções**, defina a severidade da regra como **nenhuma**.

- Do **Editor de conjunto de regras**

  Para suprimir uma violação do editor de conjunto de regras, desmarque a caixa ao lado de seu nome ou defina a **ação** como **nenhum**.

- No **Editor de código**

  Para suprimir uma violação do editor de código, coloque o cursor na linha de código com a violação e pressione **Ctrl**+ **.** para abrir o menu **ações rápidas** . Selecione **suprimir CAXXXX** > **na origem/no arquivo de supressão**.

  ![Suprimir diagnóstico do menu de ações rápidas](media/suppress-diagnostic-from-editor.png)

- Da **lista de erros**

  Você pode suprimir um ou vários diagnósticos do **lista de erros** selecionando aqueles que deseja suprimir e, em seguida, clicando com o botão direito do mouse e selecionando **suprimir** > **na origem/no arquivo de supressão**.

  - Se você suprimir **na origem**, a caixa de diálogo **Visualizar alterações** será aberta e mostrará uma visualização do C# [aviso de #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) ou Visual Basic diretiva de [aviso de #Disable](/dotnet/visual-basic/language-reference/directives/directives) que é adicionada ao código-fonte.

    ![Visualização da adição de #pragma Aviso no arquivo de código](media/pragma-warning-preview.png)

  - Se você selecionar **no arquivo de supressão**, a caixa de diálogo **Visualizar alterações** será aberta e mostrará <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> uma visualização do atributo que é adicionado ao arquivo de supressões global.

    ![Visualização da adição do atributo SuppressMessage ao arquivo de supressão](media/preview-changes-in-suppression-file.png)

  Na caixa de diálogo **Visualizar alterações** , selecione **aplicar**.

  > [!NOTE]
  > Se você não vir a opção de menu suprimir em **Gerenciador de soluções**, a violação provavelmente será proveniente da compilação e não da análise dinâmica. O **lista de erros** exibe diagnósticos ou violações de regra, tanto da análise de código ao vivo quanto da compilação. Como o diagnóstico de compilação pode ser obsoleto, por exemplo, se você tiver editado o código para corrigir a violação, mas não tiver recriado, não poderá suprimir esses diagnósticos do **lista de erros**. Os diagnósticos da análise ao vivo ou do IntelliSense estão sempre atualizados com as fontes atuais e podem ser suprimidos no **lista de erros**. Para excluir o diagnóstico de *compilação* da sua seleção, alterne o filtro de origem **lista de erros** do **Build + IntelliSense** **somente para IntelliSense**. Em seguida, selecione o diagnóstico que você deseja suprimir e continue conforme descrito anteriormente.
  >
  > ![Lista de Erros filtro de origem no Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Uso da linha de comando

Quando você cria seu projeto na linha de comando, violações de regra aparecem na saída da compilação se as seguintes condições forem atendidas:

- Os analisadores são instalados como um pacote NuGet e não como uma extensão VSIX.

- Uma ou mais regras são violadas no código do projeto.

- A [severidade](#rule-severity) de uma regra violada é definida como **aviso**; nesse caso, as violações não causam a falha da compilação ou **erros**, caso em que as violações causam a falha da compilação.

O detalhamento da saída da compilação não afeta se as violações de regra são mostradas. Mesmo com detalhes silenciosos, violações de regra aparecem na saída da compilação.

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

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores de código no Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar um bug do analisador de código](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usar conjuntos de regras](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir avisos de análise de código](../code-quality/in-source-suppression-overview.md)
