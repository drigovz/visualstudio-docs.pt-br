---
title: 'Tutorial: estender um aplicativo de console C# simples'
description: Saiba como desenvolver um aplicativo de console em C# no Visual Studio, passo a passo.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aae83c43a106fd68b03a83124ad2ddcea4652c8d
ms.sourcegitcommit: c620d59578db1b89f80e64ae04b4898bc4ab292d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377135"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Tutorial: estender um aplicativo de console C# simples

Neste tutorial, você aprenderá a usar o Visual Studio para estender o aplicativo de console criado na primeira parte. Você aprenderá alguns dos recursos do Visual Studio que o ajudarão a ser mais produtivo como desenvolvedor, como o uso de recursos do editor avançado e a depuração.

Se você acabou de concluir a [primeira parte](tutorial-console.md) desta série, você já tem o aplicativo de console da calculadora.  Para ignorar a parte 1, você pode começar abrindo o projeto de um repositório GitHub. O aplicativo de calculadora do C# está no [repositório vs-tutorial-Samples](https://github.com/MicrosoftDocs/vs-tutorial-samples), portanto, você pode apenas seguir as etapas no [tutorial: abrir um projeto de um repositório](../tutorial-open-project-from-repo.md) para começar.

## <a name="add-a-new-project"></a>Adicionar um novo projeto

O código do mundo real envolve muitos projetos trabalhando juntos em uma solução. Agora, vamos adicionar outro projeto ao aplicativo Calculator. Essa será uma biblioteca de classes que fornece algumas das funções de calculadora.

1. No Visual Studio, você pode usar o **arquivo**de comando de menu de nível superior  >  **Adicionar**  >  **novo projeto** para adicionar um novo projeto, mas você também pode clicar com o botão direito do mouse no nome do projeto existente (chamado de "nó do projeto") e abrir o menu de atalho do projeto (ou menu de contexto). Esse menu de atalho contém várias maneiras de adicionar funcionalidade aos seus projetos. Portanto, clique com o botão direito do mouse no nó do projeto em **Gerenciador de soluções**e escolha **Adicionar**  >  **novo projeto**.

1. Escolha a biblioteca de classes de modelo de projeto C# **(.net Standard)**.

   ![Captura de tela de seleção de modelo de projeto de biblioteca de classes](media/vs-2019/calculator2-add-project-dark.png)

1. Digite o nome do projeto **CalculatorLibrary**e escolha **criar**. O Visual Studio cria o novo projeto e o adiciona à solução.

   ![Captura de tela de Gerenciador de Soluções com o projeto de biblioteca de classes CalculatorLibrary adicionado](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Em vez de ter *Class1.cs*, renomeie o arquivo **CalculatorLibrary.cs**. Você pode clicar no nome em **Gerenciador de soluções** para renomeá-lo ou clicar com o botão direito do mouse e escolher **renomear**ou pressionar a tecla **F2** .

   Você pode receber uma pergunta se deseja renomear todas as referências a `Class1` no arquivo. Não importa como você responde, já que você substituirá o código em uma etapa futura.

1. Agora, precisamos adicionar uma referência de projeto, para que o primeiro projeto possa usar APIs expostas pela nova biblioteca de classes.  Clique com o botão direito do mouse no nó **referências** no primeiro projeto e escolha **Adicionar referência de projeto**.

   ![Captura de tela do item de menu Adicionar referência de projeto](media/vs-2019/calculator2-add-project-reference-dark.png)

   A caixa de diálogo **Gerenciador de Referências** é exibida. Essa caixa de diálogo permite que você adicione referências a outros projetos, bem como assemblies e DLLs COM que seus projetos precisam.

   ![Captura de tela da caixa de diálogo Gerenciador de referências](media/vs-2019/calculator2-ref-manager-dark.png)

1. Na caixa de diálogo **Gerenciador de referências** , marque a caixa de seleção do projeto **CalculatorLibrary** e escolha **OK**.  A referência do projeto é exibida em um nó **projetos** no **Gerenciador de soluções**.

   ![Captura de tela de Gerenciador de Soluções com referência de projeto](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. Em *Program.cs*, selecione a `Calculator` classe e todo o seu código e pressione **Ctrl + X** para recortá-lo de Program.cs. Em seguida, em **CalculatorLibrary**, em *CalculatorLibrary.cs*, Cole o código no `CalculatorLibrary` namespace. Em seguida, torne a classe Calculator `public` para expô-la fora da biblioteca. O código em *CalculatorLibrary.cs* agora deve ser semelhante ao seguinte código:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
        {
            public static double DoOperation(double num1, double num2, string op)
            {
                double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

                // Use a switch statement to do the math.
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
                        // Ask the user to enter a non-zero divisor.
                        if (num2 != 0)
                        {
                            result = num1 / num2;
                        }
                        break;
                    // Return text for an incorrect option entry.
                    default:
                        break;
                }
                return result;
            }
        }
    }
   ```

1. O primeiro projeto tem uma referência, mas você verá um erro que a chamada calculadora. DoOperation não resolve. Isso ocorre porque CalculatorLibrary está em um namespace de diferença, portanto, adicione `CalculatorLibrary` o namespace para uma referência totalmente qualificada.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Em vez disso, tente adicionar uma diretiva using ao início do arquivo:

   ```csharp
   using CalculatorLibrary;
   ```

   Essa alteração deve permitir que você remova o namespace CalculatorLibrary do site de chamada, mas agora há uma ambiguidade. É `Calculator` a classe em CalculatorLibrary ou é a calculadora do namespace?  Para resolver a ambiguidade, renomeie o namespace `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Bibliotecas .NET de referência: gravar em um log

1. Suponha que agora você queira adicionar um log de todas as operações e gravá-la em um arquivo de texto. A `Trace` classe .NET fornece essa funcionalidade. (Também é útil para as técnicas básicas de depuração de impressão.)  A classe Trace está em System. Diagnostics, portanto, comece adicionando uma diretiva using:

   ```csharp
   using System.Diagnostics;
   ```

1. Observando como a classe Trace é usada, você precisa manter em uma referência para a classe, que está associada a um FileStream. Isso significa que a calculadora funcionaria melhor como um objeto, então vamos adicionar um construtor.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. E precisamos alterar o `DoOperation` método estático para um método de membro.  Vamos também adicionar a saída a cada cálculo para o log, para que a dooperação se pareça com o seguinte código:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Agora, de volta ao Program.cs, a chamada estática é sinalizada com um ondulado vermelho. Para corrigi-lo, crie uma `calculator` variável adicionando a seguinte linha logo antes do loop While:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   E modifique o site de chamada da seguinte `DoOperation` maneira:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Execute o programa novamente e, quando terminar, clique com o botão direito do mouse no nó do projeto e escolha **abrir pasta no explorador de arquivos**e navegue para baixo no explorador de arquivos até a pasta de saída. Pode ser *bin/Debug/netcoreapp 3.1*e abrir o arquivo *Calculator. log* .

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Adicionar um pacote NuGet: gravar em um arquivo JSON

1. Agora suponha que desejamos gerar as operações em um formato JSON, um formato popular e portátil para armazenar dados de objeto. Para implementar essa funcionalidade, precisaremos fazer referência ao pacote NuGet Newtonsoft.Jsno. Os pacotes NuGet são o principal veículo para a distribuição de bibliotecas de classes .NET. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó **referências** para o projeto CalculatorLibrary e escolha **gerenciar pacotes NuGet**.

   ![Captura de tela de gerenciar pacotes NuGet no menu de atalho](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   O Gerenciador de pacotes NuGet é aberto.

   ![Captura de tela do Gerenciador de Pacotes NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Procure Newtonsoft.Jsno pacote e escolha **instalar**.

   ![Captura de tela das informações do pacote NuGet do Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   O pacote é baixado e adicionado ao seu projeto e uma nova entrada é exibida no nó referências em **Gerenciador de soluções**.

1. Adicione uma diretiva using para o Newtonsoft.Jsno pacote no início do *CalculatorLibrary.cs*.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Agora, substitua o construtor da calculadora pelo código a seguir e crie o objeto do membro JsonWriter:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. Modifique o `DoOperation` método para adicionar o código do gravador JSON:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Você precisará adicionar um método para concluir a sintaxe JSON quando o usuário terminar de inserir dados de operação.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. E, no *Program.cs*, adicione uma chamada para concluir no final.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Compile e execute o aplicativo e, depois de terminar de inserir algumas operações, feche o aplicativo corretamente usando o comando ' n'.  Agora, abra o consolelog.jsno arquivo e você verá algo semelhante ao seguinte:

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="next-steps"></a>Próximas etapas

Parabéns por concluir este tutorial. Para saber ainda mais, acompanhe os tutoriais a seguir.

> [!div class="nextstepaction"]
> [Continuar com mais tutoriais do C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Continuar com a visão geral do IDE do Visual Studio](/../visual-studio-ide.md)

## <a name="see-also"></a>Confira também

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Aprenda a depurar o código C# no Visual Studio](tutorial-debugger.md)
