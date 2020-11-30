---
title: Teste da cobertura do código
description: Saiba como usar o recurso cobertura de código do Visual Studio para determinar qual proporção de seu código de projeto está sendo testada por testes codificados.
ms.custom: SEO-VS-2020
ms.date: 07/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2c7bcb270184bcc140dbadef63af1315df765dc
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330050"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Usar a cobertura de código para determinar quanto do código está sendo testado

Para determinar que proporção do código do projeto está sendo testada de fato por testes codificados, como os testes de unidade, você pode usar o recurso de cobertura de código do Visual Studio. Para se proteger efetivamente contra bugs, os testes devem utilizar ou "cobrir" uma grande proporção de seu código.

A análise de cobertura de código pode ser aplicada ao código gerenciado (CLI) e não gerenciado (nativo).

A cobertura de código é uma opção quando você executa métodos de teste usando o Gerenciador de Testes. A tabela de resultados mostra a porcentagem do código que foi executada em cada assembly, classe e método. Além disso, o editor de código-fonte mostra que código foi testado.

::: moniker range="vs-2017"

![Resultados da cobertura de código com coloração](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>Requisitos

O recurso de cobertura de código está disponível apenas no Visual Studio Enterprise.

## <a name="analyze-code-coverage"></a>Analisar a cobertura de código

::: moniker range="vs-2017"

1. No menu **Teste**, escolha **Analisar Cobertura de Código**.

::: moniker-end

::: moniker range=">=vs-2019"

1. No menu **testar** , selecione **analisar cobertura de código para todos os testes**.

   ![Analisar o menu de cobertura de código no VS 2019](../test/media/vs-2019/analyze-code-coverage.png)

   Você também pode executar a cobertura de código na janela de ferramentas do Gerenciador de testes.

::: moniker-end

2. Após a execução dos testes, para ver quais linhas foram executadas, escolha ![ mostrar o ícone de colorização de cobertura de código ](../test/media/codecoverage-showcoloringicon.png) **Mostrar cores de cobertura de código** na janela resultados da cobertura de **código** . Por padrão, o código coberto por testes é realçado em azul claro.

   > [!TIP]
   > Para alterar as cores ou usar a face em negrito, escolha **ferramentas**  >  **Opções**  >  **Environment**  >  **fontes e cores**  >  **do ambiente Mostrar configurações para: editor de texto**. Em **Exibir itens**, ajuste as configurações para os itens de "cobertura", por exemplo, **área de cobertura não** coberta.
   >
   > ![Fontes e cores de cobertura de código](media/vs-2019/coverage-fonts-and-colors.png)

3. Se os resultados mostrarem baixa cobertura, investigue quais partes do código não estão sendo utilizadas e escreva mais testes para abrangê-las. As equipes de desenvolvimento normalmente desejam uma cobertura de código de aproximadamente 80%. Em algumas situações, uma cobertura menor é aceitável. Por exemplo, uma cobertura menor é aceitável onde um código é gerado a partir de um modelo padrão.

> [!TIP]
> - Desativar a otimização do compilador
> - Se você estiver trabalhando com código não gerenciado (nativo), use uma compilação de depuração
> - Gerar arquivos. PDB (símbolo) para cada assembly

Se você não obtiver os resultados esperados, confira [Solução de problemas da cobertura de código](../test/troubleshooting-code-coverage.md).

Não se esqueça de executar novamente a cobertura de código depois de atualizar seu código. Os resultados de cobertura e a coloração de código não serão atualizados automaticamente depois que você alterar o código ou executar os testes.

## <a name="report-in-blocks-or-lines"></a>Relatórios em blocos ou linhas

A cobertura de código é contada em *blocos*. Um bloco é uma parte do código com exatamente um ponto de entrada e de saída.  Se o fluxo de controle do programa passar por um bloco durante a execução de teste, esse bloco será considerado coberto. O número de vezes que o bloco é usado não tem efeito sobre o resultado.

Você também pode ter os resultados exibidos em termos de linhas escolhendo **Adicionar/Remover Colunas** no cabeçalho da tabela. Alguns usuários preferem uma contagem de linhas porque as porcentagens correspondem mais aproximadamente ao tamanho dos fragmentos que você vê no código-fonte. Um bloco longo de cálculo contaria como um único bloco mesmo se ocupar muitas linhas.

> [!TIP]
> Uma linha de código pode conter mais de um bloco de código. Se for o caso e a execução de teste utilizar todos os blocos de código na linha, isso será contado como uma linha. Se alguns blocos de código, mas não todos, na linha forem utilizados, isso será contado como uma linha parcial.

## <a name="manage-code-coverage-results"></a>Gerenciar resultados da cobertura de código

A janela **resultados da cobertura de código** geralmente mostra o resultado da execução mais recente. Os resultados podem variar se você alterar os dados de teste ou, se você executar apenas alguns dos testes cada vez.

A janela de cobertura de código também pode ser usada para exibir os resultados anteriores ou os resultados obtidos em outros computadores.

É possível mesclar os resultados de várias execuções, por exemplo, das execuções que usam dados de teste diferentes.

- **Para exibir um conjunto de resultados anterior**, selecione-o no menu suspenso. O menu mostra uma lista temporária que foi desmarcada quando você abrir uma nova solução.

- **Para exibir os resultados de uma sessão anterior**, escolha **importar resultados da cobertura de código**, navegue até a pasta **TestResults** em sua solução e importe um arquivo *. coverage* .

   A cor da cobertura poderá estar incorreta se o código-fonte tiver sido alterado desde que o arquivo *. coverage* foi gerado.

- **Para tornar os resultados legíveis como texto**, escolha **Exportar Resultados da Cobertura de Código**. Isso gera um arquivo *. coveragexml* legível, que você pode processar com outras ferramentas ou enviar facilmente por email.

- **Para enviar resultados para outra** pessoa, envie um arquivo *. Coverage* ou um arquivo *. coveragexml* exportado. A pessoa poderá importar o arquivo. Se ela tiver a mesma versão do código-fonte, poderá consultar a coloração de cobertura.

## <a name="merge-results-from-different-runs"></a>Mesclar resultados de execuções diferentes

Em algumas situações, os blocos diferentes em seu código serão usados dependendo dos dados de teste. Portanto, você pode querer combinar os resultados de execuções de testes diferentes.

Por exemplo, suponhamos que, ao executar um teste com a entrada “2 ", você descobre que 50% de uma função específica está coberta. Quando você executa o teste uma segunda vez com a entrada "-2 ", vê na exibição de cores de cobertura que os outros 50% da função estão cobertos. Agora você mescla os resultados das duas execuções de testes, e a exibição do relatório e da coloração de cobertura mostra que 100% da função foi coberta.

Use o ![ícone do botão Mesclar na janela Cobertura de Código](../test/media/codecoverage-mergeicon.png) **Mesclar Resultados da Cobertura de Código** para fazer isso. Você pode escolher qualquer combinação de execuções recentes ou resultados importados. Se você quiser combinar resultados exportados, importe-os primeiro.

Use **Exportar Resultados da Cobertura de Código** para salvar os resultados de uma operação de mesclagem.

### <a name="limitations-in-merging"></a>Limitações na mesclagem

- Se você mesclar dados de cobertura de versões diferentes do código, os resultados serão mostrados separadamente, mas não combinados. Para obter resultados totalmente combinados, use a mesma compilação do código, alterando apenas os dados do teste.

- Se você combinar um arquivo de resultados que foi exportado e depois importado, só poderá exibir os resultados por linhas, não por blocos. Use o comando **Adicionar/Remover Colunas** para mostrar os dados da linha.

- Se você combinar os resultados dos testes de um projeto do ASP.NET, os resultados dos testes separados serão exibidos, mas não combinados. Isso se aplica apenas aos artefatos do ASP.NET em si: os resultados dos outros assemblies serão combinados.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Excluir elementos dos resultados da cobertura de código

Você pode excluir elementos específicos em seu código das pontuações de cobertura, por exemplo, se o código é gerado a partir de um modelo de texto. Adicione o atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> a qualquer um dos seguintes elementos de código: class, struct, method, property, property setter ou getter, event.

> [!TIP]
> Excluir uma classe não exclui as classes derivadas.

Por exemplo:

```csharp
using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }
```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>Excluir elementos em código C++ Nativo

Para excluir os elementos não gerenciados (nativos) em código C++:

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

Use as seguintes macros:

`ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`

`ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`

- *ExclusionName* é qualquer nome exclusivo.

- *FunctionName* é um nome de função totalmente qualificado. Pode conter curingas. Por exemplo, para excluir todas as funções de uma classe, escreva `MyNamespace::MyClass::*`

- *SourceFilePath* é o local ou o caminho UNC de um arquivo .cpp. Pode conter curingas. O exemplo a seguir exclui todos os arquivos em um diretório específico: `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Coloque as chamadas para as macros de exclusão no namespace global, não em qualquer namespace ou classe.

- Você pode colocar as exclusões no arquivo de código de teste de unidade ou no arquivo de código do aplicativo.

- As exclusões devem ser criadas como o código não gerenciado (nativo), definindo a opção de compilador ou usando `#pragma managed(off)`.

> [!NOTE]
> Para excluir funções em código C++/CLI, aplique o atributo `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` à função. Esse é o mesmo para o C#.

### <a name="include-or-exclude-additional-elements"></a>Incluir ou excluir elementos adicionais

A análise de cobertura de código é executada somente em assemblies que são carregados e para os quais um arquivo *. pdb* está disponível no mesmo diretório que o arquivo *. dll* ou *. exe* . Portanto, em algumas circunstâncias, você pode estender o conjunto de assemblies que está incluído obtendo cópias dos arquivos *. pdb* apropriados.

Você pode exercer mais controle sobre quais assemblies e elementos são selecionados para análise de cobertura de código escrevendo um arquivo *. RunSettings* . Por exemplo, você pode excluir os assemblies de tipos específicos sem precisar adicionar atributos às suas classes. Para obter mais informações, confira [Personalizar a análise de cobertura de código](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analisar a cobertura de código no Azure Pipelines

Quando você faz check-in de seu código, os testes são executados no servidor de compilação, juntamente com os testes de outros membros da equipe. É útil analisar a cobertura de código no Azure Pipelines para obter o panorama mais recente e abrangente da cobertura no projeto inteiro. Isso também inclui os testes automatizados do sistema e outros testes codificados que normalmente não são executados nos computadores de desenvolvimento. Saiba mais em [Executar testes de unidade com builds](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analisar a cobertura de código na linha de comando

Para executar testes da linha de comando, use *vstest.console.exe*. A cobertura de código é uma opção do utilitário *vstest.console.exe* .

1. Iniciar o Prompt de Comando do Desenvolvedor para o Visual Studio:

   ::: moniker range="vs-2017"

   No menu **Iniciar** do Windows, escolha **Visual Studio 2017** > **Prompt de Comando do Desenvolvedor para VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   No menu **Iniciar** do Windows, escolha **Visual Studio 2019** > **Prompt de Comando do Desenvolvedor para VS 2019**.

   ::: moniker-end

2. No prompt de comando, execute o seguinte comando:

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Para obter mais informações, consulte [Opções de linha de comando de VSTest.Console.exe](vstest-console-options.md).

## <a name="troubleshoot"></a>Solucionar problemas

Se os resultados da cobertura de código não forem exibidos, o artigo [Solução de problemas de cobertura de código](../test/troubleshooting-code-coverage.md) poderá ajudá-lo.

## <a name="see-also"></a>Confira também

- [Personalizar a análise de cobertura de código](../test/customizing-code-coverage-analysis.md)
- [Solução de problemas de cobertura de código](../test/troubleshooting-code-coverage.md)
- [Teste de unidade em seu código](../test/unit-test-your-code.md)
