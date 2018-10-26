---
title: 'Tutorial: Depurar código gerenciado e nativo (modo misto)'
description: Saiba como depurar uma DLL nativa de um aplicativo .NET Core ou .NET Framework usando a depuração de modo misto
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 97ad3b6e112a05db817f7a522c3865893d439fd7
ms.sourcegitcommit: 12d6398c02e818de4fbcb4371bae9e5db6cf9509
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050320"
---
# <a name="tutorial-debug-managed-and-native-code-in-the-same-debugging-session"></a>Tutorial: Depurar código gerenciado e nativo na mesma sessão de depuração

Visual Studio permite que você habilitar mais de um tipo de depurador durante a depuração, que é chamado de depuração de modo misto. Neste tutorial, você deve definir opções para depurar código gerenciado e nativo em uma única sessão de depuração. Este tutorial mostra como depurar código nativo de um aplicativo gerenciado, mas você também pode fazer o inverso, e [depurar código gerenciado de um aplicativo nativo](../debugger/how-to-debug-in-mixed-mode.md). O depurador também oferece suporte a outros tipos de depuração de modo misto, como a depuração [Python e o código nativo](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) e usando o depurador de scripts em tipos de aplicativo, como o ASP.NET.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Criar uma DLL nativa simple
> * Criar um aplicativo simples do .NET Core ou .NET Framework para chamar a DLL
> * Inicie o depurador
> * Um ponto de interrupção no aplicativo gerenciado
> * Intervir no código nativo

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter instalado o Visual Studio e o **desenvolvimento para Desktop com C++** carga de trabalho.

    Se você ainda não instalou o Visual Studio, vá para o [downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) página para instalá-lo gratuitamente.

    Se você precisar instalar a carga de trabalho, mas já tiver o Visual Studio, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo projeto**. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento para desktop com C++** e, em seguida, selecione **Modificar**.

* Você deve também ter o **desenvolvimento de área de trabalho do .NET** carga de trabalho ou o **.NET Core desenvolvimento multiplataforma** a carga de trabalho instalada, dependendo do tipo de qual aplicativo você deseja criar.

## <a name="create-a-simple-native-dll"></a>Criar uma DLL nativa simple

1. No Visual Studio, escolha **arquivo** > **New** > **projeto**.

1. No **novo projeto** diálogo caixa, escolha **Visual C++**, **outros** na seção modelos instalados e, em seguida, no painel central, selecione **projeto vazio** .

1. No **nome** , digite **Mixed_Mode_Debugging** e clique em **Okey**.

    Visual Studio cria o projeto vazio, o que é exibido no Gerenciador de soluções, no painel direito.

1. No Gerenciador de soluções, clique com botão direito do **arquivos de origem** nó em C++ do projeto e, em seguida, escolha **Add** > **Novo Item**e, em seguida, selecione **C++ arquivo (. cpp)**. Dê ao arquivo o nome **Mixed_Mode.cpp**e escolha **Add**.

    Visual Studio adiciona o novo arquivo C++.

1. Copie o seguinte código para *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. No Gerenciador de soluções, clique com botão direito do **arquivos de cabeçalho** nó em C++ do projeto e, em seguida, escolha **Add** > **Novo Item**e, em seguida, selecione  **O arquivo de cabeçalho (. h)**. Dê ao arquivo o nome **Mixed_Mode.h**e escolha **Add**.

    Visual Studio adiciona o novo arquivo de cabeçalho.

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

1. Na barra de ferramentas de depuração, selecione uma **Debug** configuração e **x86** ou **x64** como a plataforma (para .NET Core, que sempre é executado no modo de 64 bits, selecione **x64**  como a plataforma).

1. No Gerenciador de soluções, clique com botão direito no nó do projeto (**Mixed_Mode_Debugging**) e escolha **propriedades**.

    > [!IMPORTANT]
    > Configuração de propriedade para C++ é por plataforma. Assim, se você alternar de um para a outra (x86 para x64 ou vice-versa), você também deve definir as propriedades para a nova configuração. (Na página de propriedades, verifique **x64** ou **Win32** é definida como a plataforma na parte superior da página.)

1. No **propriedades** , escolha **propriedades de configuração** > **vinculador** > **avançado**, e em seguida, nos **nenhum ponto de entrada** suspensa lista, certifique-se de que **não** está selecionado. Se você precisar alterar a configuração para **nenhuma**, em seguida, escolha **aplicar**.

1. No **propriedades** , escolha **propriedades de configuração** > **geral**e, em seguida, selecione **biblioteca dinâmica (. dll)** partir de **tipo de configuração** campo. Em seguida, aplica configurações.

    ![Alternar para uma DLL nativa](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Clique com botão direito no projeto e escolha **Build**.

    O projeto deve ser compilado sem erros.

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>Criar um aplicativo simples do .NET Framework ou .NET Core para chamar a DLL

1. No Visual Studio, escolha **arquivo** > **New** > **projeto**.

    > [!NOTE]
    > Embora você também pode adicionar o novo projeto gerenciado para a solução com o projeto C++, em vez de criar uma nova solução, não estamos fazendo que aqui para dar suporte a um conjunto maior de cenários de depuração.

1. Escolha um modelo para o código do aplicativo.

    Para o .NET Framework, no **novo projeto** diálogo caixa, escolha **Visual c#**, **área de trabalho do Windows** da seção de modelos instalados e, em seguida, no painel central, selecione  **Aplicativo do console (.NET Framework)**.

    Para o .NET Core na **novo projeto** caixa de diálogo, escolha **Visual c#**, **.NET Core** na seção modelos instalados e, em seguida, no painel central, selecione  **Aplicativo (.NET Core) do console**.

1. No **nome** , digite **Mixed_Mode_Calling_App** e clique em **Okey**.

    Visual Studio cria o projeto de console, que é exibido no Gerenciador de soluções, no painel direito.

1. Na *Program.cs*, substitua o código padrão pelo código a seguir:

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

1. No novo código, atualize o caminho do arquivo para o caminho para a DLL que você criou anteriormente (consulte comentários do código). Verifique se você substituir a *nome de usuário* espaço reservado.

## <a name="configure-mixed-mode-debugging-net-framework"></a>Configurar o modo misto de depuração (.NET Framework)

1. No Gerenciador de soluções, clique com botão direito gerenciado **Mixed_Mode_Calling_App** do projeto e escolha **definir como projeto de inicialização**.

1. Clique com botão direito gerenciado **Mixed_Mode_Calling_App** do projeto e, em seguida, escolha **propriedades**e, em seguida, escolha **depurar** no painel esquerdo. Selecione **habilitar a depuração de código nativo**e, em seguida, feche a página de propriedades para salvar as alterações.

    ![Habilitar a depuração de modo misto](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>Configurar o modo misto de depuração (.NET Core)

Na maioria das versões do Visual Studio 2017, você deve habilitar a depuração de modo misto para código nativo em um aplicativo .NET Core usando o *launchsettings. JSON* do arquivo em vez da **propriedades** página. Para acompanhar as atualizações da interface do usuário para esse recurso, consulte [problema do GitHub](https://github.com/dotnet/project-system/issues/1125).

1. Abra o *launchsettings. JSON* arquivo na *propriedades* pasta. Por padrão, você pode encontrar o arquivo nesse local.

    *C:\Users\<username > \source\repos\Mixed_Mode_Calling_App\Properties*

    Se o arquivo não estiver presente, abra as propriedades do projeto (clique com botão direito gerenciado **Mixed_Mode_Calling_App** do projeto no Gerenciador de soluções e selecione **propriedades**). Fazer uma alteração temporária na **depurar** guia e compilar seu projeto. Reverta a alteração que você fez.

1. No *lauchsettings.json* arquivo, adicione a seguinte propriedade:

    ```csharp
    "nativeDebugging": true
    ```

    Assim, por exemplo, o arquivo pode parecer com o seguinte:

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

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Definir um ponto de interrupção e iniciar o depurador

1. No projeto do c#, abra *Program.cs* e defina um ponto de interrupção na seguinte linha de código clicando na margem esquerda:

    ```csharp
    int result = Multiply(7, 7);
    ```

    Um círculo vermelho aparece na margem esquerda para indicar que você definiu o ponto de interrupção.

1. Pressione **F5** (**Debug** > **iniciar depuração**) para iniciar o depurador.

    O depurador pausa no ponto de interrupção que você definir. Uma seta amarela indica onde o depurador estiver em pausa.

## <a name="step-into-native-code"></a>Intervir no código nativo

1. Enquanto está em pausa no aplicativo gerenciado, pressione **F11** (**Debug** > **intervir**).

    Abre o arquivo de cabeçalho com o código nativo e você verá a seta amarela em que o depurador estiver pausado.

    ![Intervir no código nativo](../debugger/media/mixed-mode-step-into-native-code.png)

    Agora, você pode fazer coisas como conjunto e atingir pontos de interrupção e inspecionar variáveis.

1. Passe o mouse sobre as variáveis para ver seu valor.

1. Examine os **Autos** e **Locals** windows para ver a variável e seus valores.

    Enquanto está em pausa no depurador, você pode usar outros recursos do depurador, como o **Watch** janela e o **pilha de chamadas** janela.

1. Pressione **F11** novamente para Avançar a linha do depurador um.

1. Pressione **Shift + F11** (**Debug** > **depuração circular**) para continuar a execução do aplicativo e pausar novamente no aplicativo gerenciado.

1. Pressione **F5** para continuar o aplicativo.

    Parabéns! Você concluiu o tutorial sobre depuração de modo misto.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como depurar código nativo de um aplicativo gerenciado, habilitando a depuração de modo misto. Para obter uma visão geral de outros recursos do depurador, consulte o artigo a seguir:

> [!div class="nextstepaction"]
> [Introdução ao depurador](../debugger/debugger-feature-tour.md)
