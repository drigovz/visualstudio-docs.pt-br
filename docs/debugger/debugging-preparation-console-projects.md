---
title: Preparar-se para depurar projetos de console | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be22786a78c16dc9ffa05aba38075e4762485d2d
ms.sourcegitcommit: 9cfd3ef6c65f671a26322320818212a1ed5955fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68533318"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Preparação de depuração: Projetos de consoleC#( C++,, Visual Basic F#,)

A preparação para depurar um projeto de console é semelhante à preparação para depurar um projeto do Windows, com algumas considerações adicionais, como definir argumentos de linha de comando e como pausar o aplicativo para depuração. Para obter mais informações, consulte [Windows Forms aplicativos](../debugger/debugging-preparation-windows-forms-applications.md)e [preparação da depuração: Aplicativos de Windows Forms (.NET](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100))). Devido à semelhança de todos os aplicativos do console, este tópico abrange os seguintes tipos de projeto:

- C#, Visual Basic e F# aplicativo de console

- Aplicativo do Console C++ (.NET)

- Aplicativo do Console C++ (Win32)

  Um aplicativo de console usa a janela **Console** para aceitar a entrada e exibir mensagens de saída. Para gravar na janela do **console** , seu aplicativo deve usar o objeto de **console** em vez do objeto de depuração. Para gravar na janela de **Saída do Visual Studio**, use o objeto de depuração, como de costume. Confira se você sabe onde seu aplicativo está sendo gravado ou você pode procurar mensagens no local errado. Para obter mais informações, confira [Classe de console](/dotnet/api/system.console), [Classe de depuração](/dotnet/api/system.diagnostics.debug) e [Janela de Saída](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Definir argumentos de linha de comando

Talvez seja preciso especificar argumentos de linha de comando para o aplicativo de console. Para obter mais informações, consulte [configurações de projeto C++ para uma configuração de depuração](../debugger/project-settings-for-a-cpp-debug-configuration.md), [configurações de projeto para uma Visual Basic configuração de depuração](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)ou [configurações de projeto para configurações de C# depuração](../debugger/project-settings-for-csharp-debug-configurations.md).

Como todas as propriedades do projeto, esses argumentos persistem entre sessões de depuração e entre sessões do Visual Studio. Em virtude disso, se o aplicativo de console for um que você tenha depurado anteriormente, lembre-se de que pode haver argumentos das sessões anteriores inseridos na caixa de diálogo **\<Projeto> Páginas de Propriedades**.

## <a name="start-the-application"></a>Iniciar o aplicativo

 Quando alguns aplicativos do console iniciarem, eles são executados até a conclusão e, em seguida, são fechados. Esse comportamento pode não oferecer tempo suficiente para interromper a execução e a depuração. Para poder depurar um aplicativo, use um dos seguintes procedimentos para iniciar o aplicativo:

- Defina um ponto de interrupção em seu código e inicie seu aplicativo.

- Inicie seu aplicativo usando **F10** (**depurar depuração** >  **) ou** **F11** (**depurar** > **etapa em**) e, em seguida, navegue pelo código usando outras opções, como **Executar para clicar em**.

- No editor de código, clique com o botão direito do mouse em uma linha e selecione **executar até o cursor**.

  Quando você depura um aplicativo de console, inicie o aplicativo do prompt de comando em vez do Visual Studio. Nesse caso, você poderá iniciar o aplicativo de prompt de comando e anexar o depurador do Visual Studio a ele. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Quando você inicia um aplicativo de console do Visual Studio, a janela **Console** às vezes aparece por trás da janela do Visual Studio. Se você tentar iniciar o aplicativo de console do Visual Studio e nada acontecer, tente mover a janela do Visual Studio.

## <a name="see-also"></a>Consulte também
- [Depurando código nativo](../debugger/debugging-native-code.md)
- [Depurando código gerenciado](../debugger/debugging-managed-code.md)
- [Tipos de projeto do Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipos de projeto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Configurações do projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Segurança do depurador](../debugger/debugger-security.md)