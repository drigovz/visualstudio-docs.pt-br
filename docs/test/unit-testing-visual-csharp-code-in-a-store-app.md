---
title: Testes de unidade de código do Visual C#
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: jillfra
author: jillre
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 309cf408167cc463db8cde9e39d5c0fe4dbe26d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659840"
---
# <a name="unit-test-c-code"></a>Executar o teste de unidade de um código C#

Este artigo descreve uma maneira de criar testes de unidade para uma classe C# em um aplicativo UWP.

A classe **raiz** , que é a classe em teste, implementa uma função que calcula uma estimativa da raiz quadrada de um determinado número.

Este artigo demonstra o *desenvolvimento controlado por testes*. Nessa abordagem, você primeiro escreve um teste que verifica um comportamento específico no sistema que você está testando e, em seguida, escreve o código que passa no teste.

## <a name="create-the-solution-and-the-unit-test-project"></a>Criar a solução e o projeto de teste de unidade

1. No menu **Arquivo**, escolha **Novo** > **Projeto**.

2. Pesquise o modelo de projeto **Aplicativo em Branco (Universal do Windows)** e selecione-o.

3. Nomeie as **matemáticas**do projeto.

4. Em **Gerenciador de soluções**, clique com o botão direito do mouse na solução e escolha **Adicionar**  > **novo projeto**.

5. Pesquise o modelo de projeto **Aplicativo de Teste de Unidade (Universal do Windows)** e selecione-o.

6. Nomeie o projeto de teste **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Verificar se o testes são executados no Gerenciador de Testes

1. Insira um código de teste em **métodoteste1** no arquivo *unittest.cs* :

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   A classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> fornece vários métodos estáticos que você pode usar para verificar os resultados em métodos de teste.

::: moniker range="vs-2017"

2. No menu **testar** , escolha **executar** > **todos os testes**.

::: moniker-end

::: moniker range=">=vs-2019"

2. No menu **testar** , escolha **executar todos os testes**.

::: moniker-end

   O projeto de teste é compilado e executado. Seja paciente porque pode demorar um pouco. A janela **Gerenciador de Testes** é exibida e o teste é listado em **Testes Aprovados**. O painel **Resumo** na parte inferior da janela fornece mais detalhes sobre o teste selecionado.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Adicionar a classe Rooter ao projeto Matemática

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto de **matemáticas** e escolha **Adicionar**  > **classe**.

2. Dê ao arquivo da classe o nome *Rooter.cs*.

3. Adicione o seguinte código ao arquivo de classe raiz *Rooter.cs* :

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   A classe **rootr** declara um construtor e o método estimador **SquareRoot** . O método **SquareRoot** é apenas uma implementação mínima, apenas o suficiente para testar a estrutura básica da configuração de teste.

4. Adicione a palavra-chave `public` à declaração de classe **raiz** , para que o código de teste possa acessá-la.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Adicionar uma referência ao projeto

1. Adicione uma referência do projeto RooterTests ao aplicativo Maths.

    1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **RooterTests** e escolha Adicionar**referência**de  > .

    2. Na caixa de diálogo **Adicionar Referência - RooterTests**, expanda **Solução** e escolha **Projetos**. Selecione o projeto de **matemáticas** .

        ![Adicionar uma referência ao projeto Maths](../test/media/ute_cs_windows_addreference.png)

2. Adicione uma instrução `using` ao arquivo *unittest.cs* :

    1. Abra *unittest.cs*.

    2. Adicione esse código abaixo da linha `using Microsoft.VisualStudio.TestTools.UnitTesting;`:

       ```csharp
       using Maths;
       ```

3. Adicione um teste que usa a função **rootr** . Adicione o seguinte código a *unittest.cs*:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

   O novo teste é exibido no **Gerenciador de Testes**, no nó **Não Executar Testes**.

4. Para evitar um erro "conteúdo contém dois ou mais arquivos com o mesmo caminho de destino", em **Gerenciador de soluções**, expanda o nó **Propriedades** no projeto de **matemáticas** e exclua o arquivo *Default. Rd. xml* .

::: moniker range="vs-2017"

6. No **Gerenciador de Testes**, escolha **Executar Todos**.

   A solução é compilada e os testes são executados e aprovados.

   ![BasicTest passou no Gerenciador de testes](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. No **Gerenciador de testes**, escolha **executar todos os testes**.

   A solução é compilada e os testes são executados e aprovados.

   ![Teste básico aprovado no Gerenciador de testes](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Você configurou os projetos de teste e de aplicativo e verificou que pode executar testes que chamam funções no projeto de aplicativo. Agora, você pode começar a escrever testes e códigos reais.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Multiplicar os testes iterativamente e fazê-los passar

1. Adicione um novo teste chamado **RangeTest**:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > É recomendável não alterar testes que tenham sido aprovados. Em vez disso, adicione um novo teste.

2. Execute o teste **RangeTest** e verifique se ele falha.

   ![Falha de RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Imediatamente depois de escrever um teste, execute-o para verificar se ele falha. Isso ajuda a impedir a facilidade de errar ao escrever um teste que nunca falha.

3. Aprimore o código sob teste para que o novo teste seja aprovado. Altere a função **SquareRoot** em *Rooter.cs* para:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

::: moniker range="vs-2017"

4. No **Gerenciador de Testes**, escolha **Executar Todos**.

::: moniker-end

::: moniker range=">=vs-2019"

4. No **Gerenciador de testes**, escolha **executar todos os testes**.

::: moniker-end

   Os três testes agora foram aprovados.

> [!TIP]
> Desenvolva o código adicionando testes, um de cada vez. Verifique se todos os testes passaram após cada iteração.

## <a name="refactor-the-code"></a>Refatorar o código

Nesta seção, você refatoria o aplicativo e o código de teste e executa novamente os testes para garantir que eles ainda passem.

### <a name="simplify-the-square-root-estimation"></a>Simplifique a estimativa de raiz quadrada

1. Simplifique o cálculo central na função **SquareRoot** alterando uma linha de código, da seguinte maneira:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Execute todos os testes para certificar-se de que você não introduziu uma regressão. Todos eles devem ser aprovados.

> [!TIP]
> Um conjunto estável de testes de unidade aprovados garante que você não introduziu bugs quando alterou o código.

### <a name="eliminate-duplicated-code"></a>Eliminar código duplicado

O método **RangeTest** codifica o denominador da variável de *tolerância* que é passado para o método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Se você planeja adicionar testes adicionais que usam o mesmo cálculo de tolerância, o uso de um valor embutido em código em vários locais torna o código mais difícil de manter.

1. Adicione um método auxiliar privado à classe **UnitTest1** para calcular o valor de tolerância e, em seguida, chame esse método de **RangeTest**.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // Old code
        // double tolerance = expected/1000;

        // New code
        double tolerance = ToleranceHelper(expected);
    }
    ...
    ```

2. Execute **RangeTest** para garantir que ele ainda passe.

> [!TIP]
> Se você adicionar um método auxiliar a uma classe de teste e não quiser que ele apareça no **Gerenciador de testes**, não adicione o atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> ao método.

## <a name="see-also"></a>Consulte também

- [Walkthrough: desenvolvimento orientado por testes usando o Gerenciador de testes](quick-start-test-driven-development-with-test-explorer.md)
