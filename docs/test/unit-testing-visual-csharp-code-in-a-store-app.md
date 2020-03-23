---
title: Testes de unidade de código do Visual C#
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590859"
---
# <a name="unit-test-c-code"></a>Executar o teste de unidade de um código C#

Este artigo descreve uma maneira de criar testes de unidade para uma classe C# em um aplicativo UWP.

A classe **Rooter,** que é a classe em teste, implementa uma função que calcula uma estimativa da raiz quadrada de um determinado número.

Este artigo demonstra o *desenvolvimento orientado para o teste.* Nesta abordagem, primeiro você escreve um teste que verifica um comportamento específico no sistema que você está testando, e então você escreve o código que passa no teste.

## <a name="create-the-solution-and-the-unit-test-project"></a>Criar a solução e o projeto de teste de unidade

1. No menu **Arquivo**, escolha **Novo** > **Projeto**.

2. Pesquise o modelo de projeto **Aplicativo em Branco (Universal do Windows)** e selecione-o.

3. Nomeie o projeto **Matemática**.

4. No **Solution Explorer,** clique com o botão direito do mouse na solução e escolha **Adicionar** > **novo projeto**.

5. Pesquise o modelo de projeto **Aplicativo de Teste de Unidade (Universal do Windows)** e selecione-o.

6. Nomeie o projeto de teste **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Verificar se o testes são executados no Gerenciador de Testes

1. Insira algum código de teste no **TestMethod1** no arquivo *UnitTest.cs:*

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   A <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> classe fornece vários métodos estáticos que você pode usar para verificar resultados em métodos de teste.

::: moniker range="vs-2017"

2. No menu **Teste**, escolha **Executar** > **Todos os Testes**.

::: moniker-end

::: moniker range=">=vs-2019"

2. No menu **Teste,** escolha **Executar todos os testes**.

::: moniker-end

   O projeto de teste é compilado e executado. Seja paciente porque pode demorar um pouco. A janela **Test Explorer** aparece e o teste é listado em **Testes Aprovados**. O painel **Resumo** na parte inferior da janela fornece detalhes adicionais sobre o teste selecionado.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Adicionar a classe Rooter ao projeto Matemática

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **Matemática** e, em seguida, escolha **Adicionar** > **classe**.

2. Dê ao arquivo da classe o nome *Rooter.cs*.

3. Adicione o seguinte código ao arquivo *Rooter.cs* classe **Rooter:**

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

   A classe **Rooter** declara um construtor e o método estimador **SquareRoot.** O método **SquareRoot** é apenas uma implementação mínima, apenas o suficiente para testar a estrutura básica da configuração de teste.

4. Adicione `public` a palavra-chave à declaração da classe **Rooter,** para que o código de teste possa acessá-la.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Adicionar uma referência ao projeto

1. Adicione uma referência do projeto RooterTests ao aplicativo Maths.

    1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **RooterTests** e, em seguida, escolha **Adicionar** > **referência**.

    2. Na caixa de diálogo **Adicionar Referência - RooterTests**, expanda **Solução** e escolha **Projetos**. Selecione o projeto **Matemática.**

        ![Adicionar uma referência ao projeto Maths](../test/media/ute_cs_windows_addreference.png)

2. Adicione `using` uma declaração ao arquivo *UnitTest.cs:*

    1. Abra *UnitTest.cs*.

    2. Adicione esse código abaixo da linha `using Microsoft.VisualStudio.TestTools.UnitTesting;`:

       ```csharp
       using Maths;
       ```

3. Adicione um teste que use a função **Rooter.** Adicione o seguinte código a *UnitTest.cs:*

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

   O novo teste aparece no **Test Explorer** no nó Testes **não executados.**

4. Para evitar um erro "A carga contém dois ou mais arquivos com o mesmo caminho de destino", no **Solution Explorer,** expanda o nó **Propriedades** no projeto **Matemática** e, em seguida, exclua o arquivo *Default.rd.xml.*

::: moniker range="vs-2017"

6. No **Gerenciador de Testes**, escolha **Executar Todos**.

   A solução se constrói e os testes são executados e passam.

   ![BasicTest passou no Test Explorer](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. No **Test Explorer,** escolha **Executar todos os testes**.

   A solução se constrói e os testes são executados e passam.

   ![Teste básico aprovado no Test Explorer](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Você configurou os projetos de teste e aplicativo e verificou que você pode executar testes que chamam funções no projeto do aplicativo. Agora, você pode começar a escrever testes e códigos reais.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Multiplicar os testes iterativamente e fazê-los passar

1. Adicionar um novo teste chamado **RangeTest**:

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
   > É recomendável não alterar testes que tenham sido aprovados. Adicione um novo teste em vez disso.

2. Execute o teste **RangeTest** e verifique se ele falha.

   ![Falha de RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Imediatamente após escrever um teste, execute-o para verificar se ele falha. Isso ajuda a impedir a facilidade de errar ao escrever um teste que nunca falha.

3. Aprimore o código sob teste para que o novo teste seja aprovado. Altere a função **SquareRoot** em *Rooter.cs* para isso:

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

4. No **Test Explorer,** escolha **Executar todos os testes**.

::: moniker-end

   Os três testes agora foram aprovados.

> [!TIP]
> Desenvolva o código adicionando testes, um de cada vez. Verifique se todos os testes passaram após cada iteração.

## <a name="refactor-the-code"></a>Refatorar o código

Nesta seção, você refatora o aplicativo e o código de teste e, em seguida, reexecute testes para garantir que eles ainda passem.

### <a name="simplify-the-square-root-estimation"></a>Simplifique a estimativa de raiz quadrada

1. Simplifique o cálculo central na função **SquareRoot** alterando uma linha de código, da seguinte forma:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Faça todos os testes para ter certeza de que você não introduziu uma regressão. Todos eles devem passar.

> [!TIP]
> Um conjunto estável de testes de unidade aprovados garante que você não introduziu bugs quando alterou o código.

### <a name="eliminate-duplicated-code"></a>Eliminar código duplicado

O método **RangeTest** codifica o denominador *tolerance* da variável de tolerância <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> que é passada para o método. Se você planeja adicionar testes adicionais que usam o mesmo cálculo de tolerância, o uso de um valor codificado em vários locais torna o código mais difícil de manter.

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

2. Executar **RangeTest** para ter certeza de que ele ainda passa.

> [!TIP]
> Se você adicionar um método auxiliar a uma classe de teste e não quiser que <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> ele apareça no **Test Explorer,** não adicione o atributo ao método.

## <a name="see-also"></a>Confira também

- [Passo a passo: Desenvolvimento orientado por testes usando o Test Explorer](quick-start-test-driven-development-with-test-explorer.md)
