---
title: 'Tutorial: Depurar código gerenciado e nativo (modo misto)'
description: Saiba como depurar uma DLL nativa de um aplicativo .NET Core ou .NET Framework usando a depuração de modo misto
ms.custom: ''
ms.date: 11/02/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 121584611dcf0f25fa1f32a616253ecdecf04332
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295755"
---
# <a name="tutorial-debug-managed-and-native-code-in-the-same-debugging-session"></a>Tutorial: Depurar código gerenciado e nativo na mesma sessão de depuração

Visual Studio permite que você habilitar mais de um tipo de depurador em uma sessão de depuração, que é chamada de depuração de modo misto. Neste tutorial, você aprenderá a depurar código gerenciado e nativo em uma única sessão de depuração. 

Este tutorial mostra como depurar código nativo de um aplicativo gerenciado, mas você também pode [depurar código gerenciado de um aplicativo nativo](../debugger/how-to-debug-in-mixed-mode.md). O depurador também oferece suporte a outros tipos de depuração de modo misto, como a depuração [Python e o código nativo](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)e usando o depurador de scripts em tipos de aplicativo, como o ASP.NET.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Criar uma DLL nativa simple
> * Criar um aplicativo simples do .NET Core ou .NET Framework para chamar a DLL
> * Configurar a depuração de modo misto
> * Inicie o depurador
> * Um ponto de interrupção no aplicativo gerenciado
> * Entrar no código nativo

## <a name="prerequisites"></a>Pré-requisitos

Você deve ter o Visual Studio instalado, com as cargas de trabalho a seguir:
- **Desenvolvimento para desktop com C++**
- Qualquer um dos **desenvolvimento de área de trabalho do .NET** ou **.NET Core desenvolvimento multiplataforma**, dependendo de qual tipo de aplicativo que você deseja criar.

Se você não tiver o Visual Studio, vá para o [downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) página para instalá-lo gratuitamente.

Se você tiver instalado o Visual Studio, mas não tiver as cargas de trabalho que você precisa, selecione **abrir instalador do Visual Studio** no painel esquerdo do Visual Studio **novo projeto** caixa de diálogo. No instalador do Visual Studio, selecione as cargas de trabalho que você precisa e, em seguida, selecione **modificar**.

## <a name="create-a-simple-native-dll"></a>Criar uma DLL nativa simple

**Para criar os arquivos para o projeto DLL:**

1. No Visual Studio, selecione **arquivo** > **New** > **projeto**.

1. No **novo projeto** caixa de diálogo **Visual C++**, selecione **outros**e, em seguida, selecione **projeto vazio** no painel central.

1. No **nome** , digite **Mixed_Mode_Debugging**e, em seguida, selecione **Okey**.

   Visual Studio cria o projeto vazio e exibe-o em **Gerenciador de soluções**.

1. Na **Gerenciador de soluções**, selecione **arquivos de origem**e, em seguida, selecione **projeto** > **Adicionar Novo Item**. Ou, clique com botão direito **arquivos de origem** e selecione **Add** > **Novo Item**. 

1. No **Novo Item** caixa de diálogo, selecione **arquivo do C++ (. cpp)**. Tipo de **Mixed_Mode.cpp** na **nome** campo e, em seguida, selecione **adicionar**.

    O Visual Studio adiciona o novo arquivo C++ **Gerenciador de soluções**.

1. Copie o seguinte código para *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. Na **Gerenciador de soluções**, selecione **arquivos de cabeçalho**e, em seguida, selecione **projeto** > **Adicionar Novo Item**. Ou, clique com botão direito **arquivos de cabeçalho** e selecione **Add** > **Novo Item**. 

1. No **Novo Item** caixa de diálogo, selecione **arquivo de cabeçalho (. h)**. Tipo de **Mixed_Mode.h** na **nome** campo e, em seguida, selecione **adicionar**.

   O Visual Studio adiciona o novo arquivo de cabeçalho **Gerenciador de soluções**.

1. Copie o seguinte código para *Mixed_Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
        __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
            return a * b;
        }
    }
    #endif
    ```

1. Selecione **arquivo** > **Salvar tudo** ou pressione **Ctrl**+**Shift**+**S**  para salvar os arquivos.

**Para configurar e compilar o projeto DLL:**

1. Na barra de ferramentas do Visual Studio, selecione **Debug** configuração e **x86** ou **x64** plataforma. Se seu aplicativo de chamada será .NET Core, que sempre é executado no modo de 64 bits, selecione **x64** como a plataforma.

1. Na **Gerenciador de soluções**, selecione o **Mixed_Mode_Debugging** nó do projeto e selecione o **propriedades** ícone, ou clique com botão direito no nó do projeto e selecione **Propriedades**.

1. Na parte superior do **propriedades** painel, verifique se o **configuração** é definido como **Active (debug)** e o **plataforma** é o mesmo que o que você definir na barra de ferramentas: **x64**, ou **Win32** para x86 de plataforma. 

   > [!IMPORTANT]
   > Se você alternar plataforma desde **x86** à **x64** ou vice-versa, você deve reconfigurar as propriedades da nova plataforma. 

1. Sob **propriedades de configuração** no painel esquerdo, selecione **vinculador** > **avançado**e no menu suspenso próximo a **nenhum ponto de entrada**, selecione **não**. Se você tivesse que alterá-lo para **nenhuma**, selecione **aplicar**.

1. Sob **propriedades de configuração**, selecione **gerais**e no menu suspenso próximo a **tipo de configuração**, selecione **biblioteca dinâmica (. dll)**. Selecione **Apply**e, em seguida, selecione **Okey**.

   ![Alternar para uma DLL nativa](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Selecione o projeto no **Gerenciador de soluções** e, em seguida, selecione **compilação** > **compilar solução**, pressione **F7**, ou clique com botão direito o projeto e selecione **Build**.

   O projeto deve ser compilado sem erros.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Criar um aplicativo gerenciado simple para chamar a DLL

1. No Visual Studio, escolha **arquivo** > **New** > **projeto**.

   > [!NOTE]
   > Embora você também pode adicionar o novo projeto gerenciado à solução C++ existente, criando uma nova solução dá suporte a mais cenários de depuração.

1. No **novo projeto** caixa de diálogo, selecione **Visual C#** e no painel do meio:

   - Para um aplicativo do .NET Framework, selecione **aplicativo de Console (.NET Framework)**.
   
   - Para um aplicativo .NET Core, selecione **aplicativo de Console (.NET Core)**.

1. No **nome** , digite **Mixed_Mode_Calling_App**e, em seguida, selecione **Okey**.

   Visual Studio cria o projeto vazio e exibe-o em **Gerenciador de soluções**.

1. Substitua todo o código em *Program.cs* com o código a seguir:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

1. No novo código, substitua o caminho do arquivo no `[DllImport]` com seu caminho de arquivo para o *Mixed_Mode_Debugging.dll* você acabou de criar. Veja o comentário do código para obter dicas. Certifique-se de substituir os *nome de usuário* espaço reservado.

1. Selecione **arquivo** > **salve Program.cs** ou pressione **Ctrl**+**S** para salvar o arquivo.

## <a name="configure-mixed-mode-debugging"></a>Configurar a depuração de modo misto 

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Para configurar a depuração de modo misto para um aplicativo do .NET Framework 

1. Na **Gerenciador de soluções**, selecione o **Mixed_Mode_Calling_App** nó do projeto e selecione o **propriedades** ícone, ou clique com botão direito no nó do projeto e selecione **Propriedades**.

1. Selecione **Debug** no painel esquerdo, selecione o **habilitar a depuração de código nativo** caixa de seleção e, em seguida, feche a página de propriedades para salvar as alterações.

    ![Habilitar a depuração de modo misto](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Para configurar a depuração de modo misto para um aplicativo .NET Core 

Na maioria das versões do Visual Studio 2017, você deve usar o *launchsettings. JSON* arquivo em vez de propriedades do projeto para habilitar a depuração de modo misto para código nativo em um aplicativo .NET Core. Para acompanhar as atualizações da interface do usuário para esse recurso, consulte [problema do GitHub](https://github.com/dotnet/project-system/issues/1125).

1. No **Gerenciador de soluções**, expanda **Properties**e abra o *launchsettings. JSON* arquivo. 

   >[!NOTE]
   >Por padrão, *launchsettings. JSON* está em *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Se *launchsettings. JSON* não existir, selecione o **Mixed_Mode_Calling_App** project no **Gerenciador de soluções** e, em seguida, selecione o **propriedades** ícone, ou clique com botão direito no projeto e selecione **propriedades**. Fazer uma alteração temporária na **depurar** guia e compilar o projeto. Isso criará um *launchsettings. JSON* arquivo. Reverter a alteração feita na **depurar** guia.

1. No *lauchsettings.json* arquivo, adicione a seguinte linha:

    ```csharp
    "nativeDebugging": true
    ```

    O arquivo completo ficará semelhante ao seguinte exemplo:

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-debugging"></a>Defina um ponto de interrupção e iniciar a depuração

1. No C# projeto, abra *Program.cs*. Defina um ponto de interrupção clicando na margem da extrema esquerda, selecionando a linha e pressionando a seguinte linha de código **F9**, ou clicando duas vezes a linha e selecionando **ponto de interrupção**  >  **Inserir ponto de interrupção**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Um círculo vermelho aparece na margem esquerda em que você definiu o ponto de interrupção.

1. Pressione **F5**, selecione a seta verde na barra de ferramentas do Visual Studio, ou selecione **Debug** > **iniciar depuração** para iniciar a depuração.

   O depurador pausa no ponto de interrupção que você definir. Uma seta amarela indica onde o depurador estiver em pausa.

## <a name="step-in-and-out-of-native-code"></a>Etapa de entrada e saída do código nativo

1. Enquanto a depuração está em pausa no aplicativo gerenciado, pressione **F11**, ou selecione **Debug** > **intervir**.

   O *Mixed_Mode.h* arquivo de cabeçalho nativo é aberto e você verá a seta amarela em que o depurador estiver pausado.

   ![Intervir no código nativo](../debugger/media/mixed-mode-step-into-native-code.png)

1. Agora, você pode definir e usar pontos de interrupção e inspecionar variáveis no código nativo ou gerenciado.

   - Passe o mouse sobre as variáveis no código-fonte para ver seus valores.

   - Examinar a variável e seus valores na **automóveis** e **Locals** windows.

   - Enquanto está em pausa no depurador, você também pode usar o **Watch** windows e o **pilha de chamadas** janela.

1. Pressione **F11** novamente para Avançar a linha do depurador um.

1. Pressione **Shift**+**F11** ou selecione **depurar** > **depuração circular** para continuar a execução e pausar novamente no aplicativo gerenciado.

1. Pressione **F5** ou selecione a seta verde para continuar a depuração do aplicativo.

Parabéns! Você concluiu o tutorial sobre depuração de modo misto.

## <a name="next-step"></a>Próximas etapas

Neste tutorial, você aprendeu como depurar código nativo de um aplicativo gerenciado, habilitando a depuração de modo misto. Para obter uma visão geral de outros recursos do depurador, consulte:

> [!div class="nextstepaction"]
> [Introdução ao depurador](../debugger/debugger-feature-tour.md)
