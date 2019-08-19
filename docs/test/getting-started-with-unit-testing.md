---
title: Introdução ao teste de unidade
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30c67bb85a7cf72090ea37680daa12933c44b0cb
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870162"
---
# <a name="get-started-with-unit-testing"></a>Introdução ao teste de unidade

Use o Visual Studio para definir e executar testes de unidade para manter a integridade de código, assegurar a cobertura de código e localizar erros e falhas antes de seus clientes. Execute os testes de unidade frequentemente para ter certeza de que seu código está funcionando corretamente.

## <a name="create-unit-tests"></a>Criar testes de unidade

Esta seção descreve, em um alto nível, como criar um projeto de teste de unidade.

1. Abra o projeto que você deseja testar no Visual Studio.

   Para fins de demonstração em um exemplo de teste de unidade, este artigo testa um projeto "Olá, Mundo" simples. O código do exemplo para um projeto desse tipo é o seguinte:

   ```csharp
   public class Program
   {
       public static void Main()
       {
           Console.WriteLine("Hello World!");
       }
   }
   ```

1. No **Gerenciador de Soluções**, selecione o nó da solução. Em seguida, na barra de menus superior, selecione **Arquivo** > **Adicionar** > **Novo Projeto**.

1. Na caixa de diálogo Novo Projeto, localize um modelo de projeto de teste de unidade para a estrutura de teste que você deseja usar e selecione-o.

   ::: moniker range=">=vs-2019"

   ![Modelo de projeto de teste de unidade no Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Clique em **Avançar**, escolha um nome para o projeto de teste e, em seguida, clique em **Criar**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Modelo de projeto de teste de unidade no Visual Studio 2019](media/mstest-test-project-template.png)

   Escolha um nome para o projeto de teste e clique em **OK**.

   ::: moniker-end

   O projeto é adicionado à solução.

   ![Projeto de teste de unidade no Gerenciador de Soluções](media/vs-2019/solution-explorer.png)

1. No projeto de teste de unidade, adicione uma referência ao projeto que você deseja testar clicando com o botão direito do mouse em **Referências** ou **Dependências** e, em seguida, escolhendo **Adicionar Referência**.

1. Selecione o projeto que contém o código que você testará e clique em **OK**.

   ![Adicionar referência de projeto no Visual Studio](media/vs-2019/reference-manager.png)

1. Adicione código ao método de teste de unidade.

   ![Adicionar código ao método de teste de unidade no Visual Studio](media/vs-2019/unit-test-method.png)

> [!TIP]
> Confira uma explicação mais detalhada da criação de testes de unidade em [Criar e executar testes de unidade para código gerenciado](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Executar testes de unidade

1. Abra o [Gerenciador de Testes](../test/run-unit-tests-with-test-explorer.md) escolhendo **Teste** > **Windows** > **Gerenciador de Testes** na barra de menus superior.

1. Execute seus testes de unidade clicando em **Executar Tudo**.

   ![Executar testes de unidade no Gerenciador de Testes](media/vs-2019/test-explorer-run-all.png)

   Depois de concluir os testes, uma marca de seleção verde indica que houve aprovação em um teste. Um ícone "x" vermelho indica falha em um teste.

   ![Examine os resultados de teste de unidade no Gerenciador de Testes](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Você pode usar o [Gerenciador de Testes](../test/run-unit-tests-with-test-explorer.md) para executar testes de unidade do framework de testes interno (MSTest) ou de estruturas de teste de terceiros. Você pode agrupar os testes em categorias, filtrar a lista de testes, criar, salvar e executar playlists de testes. Você também pode depurar testes e analisar um teste de desempenho e cobertura de código.

## <a name="view-live-unit-test-results"></a>Exibir resultados de teste de unidade em tempo real

Se estiver usando a estrutura de teste do MSTest, do xUnit ou do NUnit no Visual Studio de 2017 ou posterior, você poderá ver os resultados em tempo real de seus testes de unidade.

> [!NOTE]
> O Live Unit Testing está disponível somente no Enterprise Edition.

1. Ative o Live Unit Testing do menu **Teste**, escolhendo **Teste** > **Live Unit Testing** > **Iniciar**.

   ::: moniker range="vs-2017"

   ![Ativar o teste de unidade em tempo real](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Iniciar o Live Unit Testing no Visual Studio 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Exiba os resultados dos testes dentro da janela do editor de código conforme você escreve e edita o código.

   ![Exibir os resultados dos testes](media/vs-2019/live-unit-testing-results.png)

1. Clique em um indicador de resultado do teste para obter mais informações, assim como os nomes dos testes que abordam esse método.

   ![Escolha os indicadores de resultados do teste](media/vs-2019/live-unit-testing-details.png)

Para obter mais informações sobre o Live Unit Testing, veja [Live Unit Testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Gerar testes de unidade com IntelliTest

Quando executa o IntelliTest, você pode ver quais testes estão falhando e adicionar o código que for necessário para corrigi-los. É possível selecionar quais dos testes gerados serão salvos em um projeto de teste para oferecer um pacote de regressão. Conforme você alterar seu código, execute novamente o IntelliTest para manter os testes gerados em sincronia com as alterações do código. Para saber como, confira [Gerar testes de unidade para seu código com o IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> O IntelliTest está disponível somente para código gerenciado direcionado ao .NET Framework.

![Gerando testes de unidade com IntelliTest](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Analisar a cobertura de código

Para determinar que proporção do código do projeto está sendo testada de fato por testes codificados, como os testes de unidade, você pode usar o recurso de cobertura de código do Visual Studio. Para se proteger efetivamente contra bugs, os testes devem usar uma grande proporção do seu código. Para saber como, confira [Usar a cobertura de código para determinar quanto do código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-third-party-test-framework"></a>Usar uma estrutura de teste de terceiros

Você pode executar testes de unidade no Visual Studio usando estruturas de teste de terceiros, como Boost, Google e NUnit. Use o **Gerenciador de Pacotes NuGet** para instalar o pacote do NuGet para a estrutura de sua escolha. Ou, para estruturas de teste NUnit e xUnit, o Visual Studio inclui modelos de projeto de teste pré-configurados que incluem os pacotes NuGet necessários.

Para criar testes de unidade que usam [NUnit](https://nunit.org/):

1. Abra a solução que contém o código que você deseja testar.

2. Clique com o botão direito do mouse na solução no **Gerenciador de Soluções** e escolha **Adicionar** > **Novo Projeto**.

3. Selecione o modelo de projeto **Projeto de Teste do NUnit**.

   ::: moniker range=">=vs-2019"

   ![Modelo de projeto de teste NUnit no Visual Studio 2019](media/vs-2019/nunit-test-project-template.png)

   Clique em **Avançar**, nomeie o projeto e clique em **Criar**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Nomeie o projeto e clique em **OK** para criá-lo.

   ::: moniker-end

   O modelo de projeto inclui referências de NuGet a NUnit e NUnit3TestAdapter.

   ![Dependências de NuGet NUnit no Gerenciador de Soluções](media/vs-2019/nunit-nuget-dependencies.png)

4. Adicione uma referência do projeto de teste ao projeto que contém o código que você deseja testar.

   Clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Adicionar** > **Referência**. (Também é possível adicionar uma referência no menu do botão direito do nó **Referências** ou **Dependências**.)

5. Adicione código ao método de teste.

   ![Adicionar o código ao arquivo de código do teste de unidade](media/vs-2019/unit-test-method.png)

6. Execute o teste do **Gerenciador de Testes** ou clicando com o botão direito do mouse no código de teste e escolhendo **Executar Testes**.

## <a name="see-also"></a>Consulte também

* [Passo a passo: Criar e executar testes de unidade para código gerenciado](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Criar comando de Testes de Unidade](create-unit-tests-menu.md)
* [Gerar testes com IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Executar testes com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md)
* [Analisar a cobertura de código](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
