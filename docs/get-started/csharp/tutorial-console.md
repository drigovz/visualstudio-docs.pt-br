---
title: 'Tutorial: Introdução aos aplicativos de console em C#'
description: Saiba como criar aplicativos de console em C# do Visual Basic no Visual Studio, passo a passo.
ms.custom: seodec18, get-started
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.prod: visual-studio-dev15
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 333eeb3f826663d979e1cec444ede7eda4b55b2a
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562211"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>Tutorial: Introdução ao aplicativo de console do C# no Visual Studio

Neste tutorial para C#, você usará o Visual Studio para criar e executar um aplicativo de console e explorar alguns recursos do [IDE (ambiente de desenvolvimento integrado) do Visual Studio](../visual-studio-ide.md) durante esse processo.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

## <a name="create-a-project"></a>Criar um projeto

Para começar, criaremos um projeto de aplicativo em C#. O tipo de projeto inclui todos os arquivos de modelo que você precisará, mesmo sem adicionar nada!

1. Abra o Visual Studio 2017.

2. Na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**.

3. Na caixa de diálogo **Novo Projeto** no painel esquerdo, expanda **C#** e escolha **.NET Core**. No painel central, escolha **Aplicativo de Console (.NET Core)**. Em seguida, nomeie o arquivo como *Calculator*.

   ![Modelo de projeto do aplicativo do console (.NET Core) na caixa de diálogo Novo projeto no IDE do Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Adicionar um grupo de trabalho (opcional)

Se o modelo de projeto **Aplicativo do Console (.NET Core)** não for exibido, você poderá obtê-lo adicionando a carga de trabalho **Desenvolvimento .NET Core de multiplataforma**. Para saber como fazer isso, confira a seção "[O que é uma carga de trabalho e como fazer para adicionar uma?](#workload)" das perguntas frequentes.

## <a name="create-the-app"></a>Criar o aplicativo

Primeiro, adicionaremos o código para criar uma calculadora básica. Em seguida, ajustaremos o código para adicionar funcionalidade. Depois disso, depuraremos o aplicativo para encontrar e corrigir erros. Por fim, refinaremos o código para torná-lo mais eficiente.

Vamos começar adicionando o código de calculadora básica ao projeto.

1. No editor de códigos, exclua o código padrão "Olá, Mundo".

    ![Excluir o código padrão Olá, Mundo do novo aplicativo de calculadora](./media/csharp-console-calculator-deletehelloworld.png)

   Especificamente, exclua todo o código visto no editor de códigos.

1. Insira ou cole o seguinte novo código no editor de códigos:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```
1. Escolha **Calculadora** para executar seu programa ou pressione **F5**.

   ![Escolha o botão Calculadora para executar o aplicativo na barra de ferramentas](./media/csharp-console-calculator-button.png)

   Uma janela do console é aberta.

1. Exiba o aplicativo na janela do console e, em seguida, siga os prompts para adicionar os números **42** e **119**.

   O aplicativo deverá ser semelhante à seguinte captura de tela:

    ![Janela do console mostrando o aplicativo de Calculadora que inclui prompts de quais ações devem ser executadas](./media/csharp-console-calculator.png)

### <a name="add-decimals"></a>Adicionar decimais

Atualmente, o aplicativo de calculadora aceita e retorna números inteiros. No entanto, ele será mais preciso se adicionarmos um código que permita decimais.

Como mostrado na captura de tela a seguir, se você executar o aplicativo e dividir o número 42 pelo número 119, o resultado será 0 (zero), o que não é exato.

![Janela do console mostrando o aplicativo de Calculadora que não retorna um numeral decimal como resultado](./media/csharp-console-calculator-nodecimal.png)

Vamos corrigir o código para que ele identifique decimais.

1. Altere cada instância da variável `int` para `float`.

   (Você pode usar o controle [Localizar e Substituir](../../ide/finding-and-replacing-text.md#find-and-replace-control) para ajudá-lo com essa tarefa. Para acessar o controle de pesquisa no editor de códigos, pressione **Crtl**+**F**. Em seguida, escolha o botão **Localizar Próximo** ou **Localizar Anterior** no controle de pesquisa. Para acessar opções de substituição, escolha o botão ao lado da caixa de texto **Localizar**. Para fazer uma substituição por vez, escolha o botão **Substituir próximo** ao lado da caixa de texto **Substituir**. Para substituir todas as correspondências, escolha o botão **Substituir Tudo**.)

1. Execute novamente o aplicativo de calculadora e divida o número **42** pelo número **119**.

   Observe que o aplicativo agora retorna um numeral decimal em vez de zero.

    ![Janela do console mostrando o aplicativo de Calculadora que agora retorna um numeral decimal como resultado](./media/csharp-console-calculator-decimal.png)

No entanto, o aplicativo produz apenas um resultado decimal. Vamos fazer mais alguns ajustes no código, de modo que o aplicativo possa calcular decimais também.

1. Altere cada instância da variável `float` para `double`.

1. Altere cada instância do método `Convert.ToInt32` para `Convert.ToDouble`.

1. Execute o aplicativo de calculadora e divida o número **42,5** pelo número **119,75**.

   Observe que o aplicativo agora aceita valores decimais e retorna um numeral decimal mais longo como resultado.

    ![Janela do console mostrando o aplicativo de Calculadora que agora aceita números decimais e retorna um numeral decimal mais longo como resultado](./media/csharp-console-calculator-usedecimals.png)

    (Corrigiremos o número de casas decimais na seção [Revisar o código](#revise-the-code).)

## <a name="debug-the-app"></a>Depurar o aplicativo

Melhoramos nosso aplicativo de calculadora básica, mas ele ainda não é à prova de falhas para tratar exceções, como erros de entrada do usuário.

Por exemplo, se você tentar dividir um número por zero ou inserir um caractere alfa quando o aplicativo esperar um caractere numérico (ou vice-versa), o aplicativo parará de funcionar e retornará um erro.

Vamos examinar alguns erros comuns de entrada do usuário, localizá-los no [depurador](../../debugger/debugger-feature-tour.md) e corrigi-los no código.

### <a name="fix-the-divide-by-zero-error"></a>Corrigir o erro de "divisão por zero"

Quando você tenta dividir um número por zero, o aplicativo de console congela. Em seguida, o Visual Studio mostra o que há de errado no editor de códigos.

   ![O editor de códigos do Visual Studio mostra o erro de divisão por zero](./media/csharp-console-calculator-dividebyzero-error.png)

Vamos alterar o código para tratar esse erro.

1. Exclua o código exibido diretamente entre `case "d":` e o comentário `// Wait for the user to respond before closing`.

1. Substitua-o pelo seguinte código:

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Depois que você adicionar o código, a seção com a instrução `switch` deverá ser semelhante à seguinte captura de tela:

   ![A seção alterada e revisada no editor de códigos do Visual Studio](./media/csharp-console-calculator-switch-code.png)

Agora, quando você dividir qualquer número por zero, o aplicativo solicitará outro número. Melhor ainda: Ele não parará de perguntar enquanto você não fornecer um número diferente de zero.

   ![O editor de códigos do Visual Studio mostra o erro de divisão por zero](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Corrigir o erro de "formato"

Se você inserir um caractere alfa quando o aplicativo esperar um caractere numérico (ou vice-versa), o aplicativo de console congelará. Em seguida, o Visual Studio mostra o que há de errado no editor de códigos.

   ![O editor de códigos do Visual Studio mostra um erro de formato](./media/csharp-console-calculator-format-error.png)

Para corrigir esse erro, precisamos refatorar o código que inserimos anteriormente.

#### <a name="revise-the-code"></a>Revisar o código

Em vez de depender da classe `program` para tratar todo o código, dividiremos nosso aplicativo em duas classes: `calculator` e `program`.  

A classe `calculator` fará a maior parte do trabalho de cálculo e a classe `program` cuidará do trabalho de captura de erros e da interface do usuário.

Vamos começar.

1. Exclua tudo *após* o seguinte bloco de código:

    ```csharp

    using System;

    namespace Calculator
    {

    ```

1. Depois, adicione uma nova classe `calculator`, da seguinte maneira:

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error

            // Use a switch statement to do the math
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Em seguida, adicione uma nova classe `program`, da seguinte maneira:

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing
            }
            return;
        }
    }
    ```
1. Escolha **Calculadora** para executar seu programa ou pressione **F5**.

1. Siga os prompts e divida o número **42** pelo número **119**. O aplicativo deverá ser semelhante ao seguinte:

    ![Janela do console mostrando o aplicativo de Calculadora refatorado que inclui prompts de quais ações devem ser executadas e tratamento de erro para entradas incorretas](./media/csharp-console-calculator-refactored.png)

    Observe que você tem a opção de inserir mais equações até optar por fechar o aplicativo de console. Além disso, reduzimos também o número de casas decimais no resultado.

## <a name="close-the-app"></a>Feche o aplicativo

1. Se você ainda não fez isso, feche o aplicativo de calculadora.

1. Feche o painel **Saída** no Visual Studio.

   ![Fechar o painel Saída no Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. No Visual Studio, pressione **Ctrl**+**S** para salvar o aplicativo.

1. Feche o Visual Studio.

## <a name="code-complete"></a>Conclusão do código

Durante este tutorial, fizemos muitas alterações no aplicativo de calculadora. O aplicativo agora manipula recursos de computação com mais eficiência e trata a maioria dos erros de entrada do usuário.

Este é o código completo, tudo em um só lugar:

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error

            // Use a switch statement to do the math
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing
            }
            return;
        }
    }
}

```

## <a name="quick-answers-faq"></a>Perguntas frequentes com respostas rápidas

Aqui estão algumas perguntas frequentes rápidas para destacar alguns conceitos principais. As perguntas frequentes também incluem respostas para perguntas que poderão surgir quando você seguir os procedimentos do tutorial.

### <a name="what-is-c"></a>O que é C#?

O C# é uma linguagem de programação fortemente tipada que é executada no .NET Framework e no .NET Core. Com o C#, você pode criar aplicativos do Windows, aplicativos cliente-servidor, aplicativos de banco de dados, serviços Web em XML, componentes distribuídos e muito mais.

### <a name="what-is-visual-studio"></a>O que é o Visual Studio?

Visual Studio é um pacote de desenvolvimento integrado de ferramentas de produtividade para desenvolvedores. Pense nele como um programa que você pode usar para criar programas e aplicativos.

### <a name="what-is-a-console-app"></a>O que é um aplicativo do console?

Um aplicativo de console obtém a entrada e exibe a saída em uma janela de linha de comando, também conhecida como um console.

### <a name="what-is-net-core"></a>O que é o .NET Core?

O .NET Core é o próximo passo na evolução do .NET Framework. Enquanto o .NET Framework pode compartilhar o código entre linguagens de programação, o .NET Core agrega a capacidade de compartilhar o código entre plataformas. Melhor ainda, ele é um software livre.

O .NET Framework e o .NET Core incluem bibliotecas de funcionalidades predefinidas. Eles também incluem um CLR (Common Language Runtime), que atua como uma máquina virtual na qual executar o código.

### <a id="workload"></a>O que é uma carga de trabalho e como fazer para adicionar uma?

Uma carga de trabalho no Visual Studio representa um conjunto de modelos e opções de programação que pode ser usado para personalizar a instalação do Visual Studio. Uma carga de trabalho instala somente as ferramentas necessárias para a linguagem de programação e a plataforma de sua escolha. Veja abaixo como instalá-las.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opção 1: Usar a caixa de diálogo Novo Projeto

1. Selecione o link **Abrir o Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.

   ![Escolha o link Abrir Instalador do Visual Studio na caixa de diálogo Novo Projeto](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento multiplaforma do .NET Core** e, em seguida, selecione **Modificar**.

   ![Carga de trabalho de desenvolvimento multiplataforma do .NET Core no Instalador do Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opção 2: Usar a barra de menus Ferramentas

1. Cancele a caixa de diálogo **Novo Projeto**; em seguida, vá até a barra de menus superior e escolha **Ferramentas** > **Obter Ferramentas e Recursos**.

1. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento multiplaforma do .NET Core** e, em seguida, selecione **Modificar**.

## <a name="next-steps"></a>Próximas etapas

Parabéns por concluir este tutorial. Para saber ainda mais, acompanhe os tutoriais a seguir.

> [!div class="nextstepaction"]
> [Tutoriais de C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Consulte também

* [Curso em vídeo Conceitos básicos do C# para iniciantes completos](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)