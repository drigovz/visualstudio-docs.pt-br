---
title: Introdução aos aplicativos de console em C# no Visual Studio
description: Saiba como criar aplicativos de console em C# do Visual Basic no Visual Studio, passo a passo.
ms.custom: ''
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: ad1ee95cb9cc754261502e7377cde6c91e5befce
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859504"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>Tutorial: Introdução ao aplicativo de console em C# no Visual Studio

Neste tutorial para C#, você usará o Visual Studio para criar e executar um aplicativo de console e explorar alguns recursos do [IDE (ambiente de desenvolvimento integrado) do Visual Studio](visual-studio-ide.md) durante esse processo.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

## <a name="create-a-project"></a>Criar um projeto

Primeiro, vamos criar um projeto de aplicativo em C#. O tipo de projeto inclui todos os arquivos de modelo que você precisará, mesmo sem adicionar nada!

1. Abra o Visual Studio 2017.

2. Na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**.

3. Na caixa de diálogo **Novo Projeto** no painel esquerdo, expanda **C#** e escolha **.NET Core**. No painel central, escolha **Aplicativo de Console (.NET Core)**. Em seguida, nomeie o arquivo como *Calculator*.

   ![Modelo de projeto do aplicativo do console (.NET Core) na caixa de diálogo Novo projeto no IDE do Visual Studio](../ide/media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Adicionar um grupo de trabalho (opcional)

Se o modelo de projeto **Aplicativo do Console (.NET Core)** não for exibido, você poderá obtê-lo adicionando a carga de trabalho **Desenvolvimento .NET Core de multiplataforma**. Você pode adicionar essa carga de trabalho de uma das duas maneiras, dependendo de quais atualizações do Visual Studio 2017 estão instaladas no seu computador.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opção 1: usar a caixa de diálogo Novo Projeto

1. Selecione o link **Abrir o Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.

   ![Escolha o link Abrir Instalador do Visual Studio na caixa de diálogo Novo Projeto](../ide/media/csharp-open-visual-studio-installer-generic-dark.png)

1. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento multiplaforma do .NET Core** e, em seguida, selecione **Modificar**.

   ![Carga de trabalho de desenvolvimento multiplataforma do .NET Core no Instalador do Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opção 2: usar a barra de menus Ferramentas

1. Cancele a caixa de diálogo **Novo Projeto**; em seguida, vá até a barra de menus superior e escolha **Ferramentas** > **Obter Ferramentas e Recursos**.

1. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento multiplaforma do .NET Core** e, em seguida, selecione **Modificar**.

## <a name="create-a-c-console-calculator-app"></a>Crie um aplicativo "Calculadora de Console em C#"

1. Abra o Visual Studio 2017 e, na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**.

1. Na caixa de diálogo **Novo Projeto** no painel esquerdo, expanda **C#** e escolha **.NET Core**. No painel central, escolha **Aplicativo de Console (.NET Core)**. Em seguida, nomeie o arquivo como *Calculator*.

1. Digite ou cole o seguinte código no editor de código:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then instantiate to zero
                double num1 = 0; double num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToDouble(Console.ReadLine());

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
                        // Ask the user to enter a non-zero divisor until they do so
                        while (num2 == 0)
                        {
                            Console.WriteLine("Enter a non-zero divisor: ");
                            num2 = Convert.ToDouble(Console.ReadLine());
                        }
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                    // Return text for an incorrect option entry
                    default:
                        Console.WriteLine("That is an incorrect option entry, please try again.");
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

   O código que aparece depois de `static void Main(string[] args)` deve ter a seguinte aparência:

   ![Editor de código mostrando a Calculadora de Console em C#](../ide/media/csharp-console-calculator-code.png)

1. Escolha **Calculadora** para executar seu programa ou pressione **F5**.

   ![Escolha o botão Calculadora para executar o aplicativo na barra de ferramentas](../ide/media/csharp-console-calculator-button.png)

1. Visualize o aplicativo na janela do console. Quando você segue as mensagens de opções, seu aplicativo deve ser semelhante à captura de tela a seguir:

    ![Janela do console mostrando o aplicativo Calculadora, que inclui as mensagens de opções com as ações que devem ser executadas.](../ide/media/csharp-console-calculator.png)

### <a name="close-the-app"></a>Feche o aplicativo

1. Pressione qualquer tecla para fechar o aplicativo da calculadora.

1. Feche o painel **Saída** no Visual Studio.

   ![Fechar o painel Saída no Visual Studio](../ide/media/csharp-calculator-close-output-pane.png)

1. Feche o Visual Studio.

## <a name="quick-answers-faq"></a>Perguntas frequentes com respostas rápidas

Aqui estão algumas perguntas frequentes rápidas para destacar alguns conceitos principais.

### <a name="what-is-c"></a>O que é C#?

O C# é uma linguagem de programação fortemente tipada que é executada no .NET Framework e no .NET Core. Com o C#, você pode criar aplicativos do Windows, aplicativos cliente-servidor, aplicativos de banco de dados, serviços Web em XML, componentes distribuídos e muito mais.

### <a name="what-is-visual-studio"></a>O que é o Visual Studio?

Visual Studio é um pacote de desenvolvimento integrado de ferramentas de produtividade para desenvolvedores. Pense nele como um programa que você pode usar para criar programas e aplicativos.

### <a name="what-is-a-console-app"></a>O que é um aplicativo do console?

Um aplicativo de console obtém a entrada e exibe a saída em uma janela de linha de comando, também conhecida como um console.

### <a name="what-is-net-core"></a>O que é o .NET Core?

O .NET Core é o próximo passo na evolução do .NET Framework. Enquanto o .NET Framework pode compartilhar o código entre linguagens de programação, o .NET Core agrega a capacidade de compartilhar o código entre plataformas. Melhor ainda, ele é um software livre.

O .NET Framework e o .NET Core incluem bibliotecas de funcionalidades predefinidas. Eles também incluem um CLR (Common Language Runtime), que atua como uma máquina virtual na qual executar o código.

## <a name="next-steps"></a>Próximas etapas

Parabéns por concluir este tutorial. Para saber ainda mais, acompanhe os tutoriais a seguir.

> [!div class="nextstepaction"]
> [Tutoriais de C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Consulte também

* [Curso em vídeo Conceitos básicos do C# para iniciantes completos](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
