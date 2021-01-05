---
title: Depurar projetos DLL | Microsoft Docs
description: Depurar arquivos da biblioteca de vínculo dinâmico (DLL) no Visual Studio. Use o Visual Studio para criar, compilar, configurar e depurar DLLs.
ms.custom: SEO-VS-2020
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec78e9a04062699ea699f45671e1210fc2306631
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728480"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Depurar DLLs no Visual Studio (C#, C++, Visual Basic, F #)

Uma DLL (biblioteca de vínculo dinâmico) é uma biblioteca que contém código e dados que podem ser usados por mais de um aplicativo. Você pode usar o Visual Studio para criar, compilar, configurar e depurar DLLs.

## <a name="create-a-dll"></a>Criar uma DLL

Os seguintes modelos de projeto do Visual Studio podem criar DLLs:

- Biblioteca de classes C#, Visual Basic ou F #
- Biblioteca do controle de Windows Forms do C# ou do Visual Basic (WCF)
- Biblioteca de Dynamic-Link C++ (DLL)

Para obter mais informações, consulte [técnicas de depuração do MFC](../debugger/mfc-debugging-techniques.md).

A depuração de uma biblioteca WCF é semelhante à depuração de uma biblioteca de classes. Para obter detalhes, consulte [controles de Windows Forms](/dotnet/framework/winforms/controls/index).

Normalmente, você chama uma DLL de outro projeto. Ao depurar o projeto de chamada, dependendo da configuração de DLL, você pode entrar e depurar o código de DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Configuração de depuração de DLL

Quando você usa um modelo de projeto do Visual Studio para criar um aplicativo, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria automaticamente as configurações necessárias para depurar e liberar as configurações de compilação. Você pode alterar essas configurações, se necessário. Para obter mais informações, consulte os seguintes artigos:

- [Configurações do projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configurações de projeto para configurações de depuração em C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Como definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Definir o C++ DebuggableAttribute

Para que o depurador seja anexado a uma DLL C++, o código C++ deve emitir `DebuggableAttribute` .

**Para definir `DebuggableAttribute` :**

1. Selecione o projeto da DLL C++ no **Gerenciador de soluções** , selecione o ícone **Propriedades** ou clique com o botão direito do mouse no projeto e selecione **Propriedades**.

1. No painel **Propriedades** , em depuração do **vinculador**  >  , selecione **Sim (/ASSEMBLYDEBUG)** para o **assembly depurável**.

Para obter mais informações, consulte [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> Definir locais de arquivo de DLL C/C++

Para depurar uma DLL externa, um projeto de chamada deve ser capaz de localizar a DLL, seu [arquivo. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e todos os outros arquivos necessários para a dll. Você pode criar uma tarefa de compilação personalizada para copiar esses arquivos para a pasta de saída do *\<project folder> \debug* ou pode copiar os arquivos manualmente.

Para projetos C/C++, você pode definir os locais de arquivo de cabeçalho e LIB nas páginas de propriedades do projeto, em vez de copiá-los para a pasta de saída.

**Para definir o cabeçalho do C/C++ e os locais do arquivo LIB:**

1. Selecione o projeto de DLL C/C++ em **Gerenciador de soluções** , selecione o ícone **Propriedades** ou clique com o botão direito do mouse no projeto e selecione **Propriedades**.

1. Na parte superior do painel **Propriedades** , em **configuração**, selecione **todas as configurações**.

1. Em   >    >  **diretórios de inclusão adicionais** gerais do C/C++, especifique a pasta que tem os arquivos de cabeçalho.

1. Em   >    >  **diretórios de bibliotecas adicionais** gerais do vinculador, especifique a pasta que tem os arquivos lib.

1. Em entrada do **vinculador**  >    >  **dependências adicionais**, especifique o caminho completo e o nome do arquivo para os arquivos lib.

1. Selecione **OK**.

Para obter mais informações sobre configurações de projeto C++, consulte [referência de página de propriedades do Windows C++](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Compilar uma versão de depuração

Certifique-se de criar uma versão de depuração da DLL antes de iniciar a depuração. Para depurar uma DLL, um aplicativo de chamada deve ser capaz de encontrar seu [arquivo. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e quaisquer outros arquivos necessários para a dll.

Você pode criar uma tarefa de compilação personalizada para copiar os arquivos DLL para a pasta de saída do *\<calling project folder> \debug* ou pode copiar os arquivos manualmente.

Certifique-se de chamar a DLL em seu local correto. Isso pode parecer óbvio, mas se um aplicativo de chamada encontrar e carregar uma cópia diferente da DLL, o depurador nunca atingirá os pontos de interrupção que você definir.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Depurar uma DLL

Você não pode executar uma DLL diretamente. Ele deve ser chamado por um aplicativo, geralmente um arquivo *. exe* . Para obter mais informações, consulte [projetos do Visual Studio-C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Para depurar uma DLL, você pode [iniciar a depuração do aplicativo de chamada](#vxtskdebuggingdllprojectsthecallingapplication)ou [depurar a partir do projeto de dll](how-to-debug-from-a-dll-project.md) especificando seu aplicativo de chamada. Você também pode usar a janela do depurador [imediato](#vxtskdebuggingdllprojectstheimmediatewindow) para avaliar funções ou métodos de dll em tempo de design, sem usar um aplicativo de chamada.

Para obter mais informações, consulte [primeira olhada no depurador](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Iniciar a depuração do aplicativo de chamada

O aplicativo que chama uma DLL pode ser:

- Um aplicativo de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto no mesmo ou em uma solução diferente da dll.
- Um aplicativo existente que já está implantado e em execução em um computador de teste ou de produção.
- Localizado na Web e acessado por meio de uma URL.
- Um aplicativo Web com uma página da Web que incorpora a DLL.

Para depurar uma DLL de um aplicativo de chamada, você pode:

- Abra o projeto para o aplicativo de chamada e inicie a depuração selecionando **depurar**  >  **Iniciar Depuração** ou pressionar **F5**.

  ou

- Anexe a um aplicativo que já está implantado e em execução em um computador de teste ou de produção. Use esse método para DLLs em sites ou em aplicativos Web. Para obter mais informações, consulte [como: anexar a um processo em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Antes de iniciar a depuração do aplicativo de chamada, defina um ponto de interrupção na DLL. Consulte [usando pontos de interrupção](../debugger/using-breakpoints.md). Quando o ponto de interrupção da DLL é atingido, você pode percorrer o código, observando a ação em cada linha. Para obter mais informações, consulte [navegar no código no depurador](../debugger/navigating-through-code-with-the-debugger.md).

Durante a depuração, você pode usar a janela **módulos** para verificar os arquivos DLLs e *. exe* que o aplicativo carrega. Para abrir a janela **módulos** , durante a depuração, selecione **depurar**  >    >  **módulos** do Windows. Para obter mais informações, consulte [como: usar a janela módulos](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Usar a janela imediata

Você pode usar a janela **imediata** para avaliar funções de dll ou métodos em tempo de design. A janela **imediata** desempenha a função de um aplicativo de chamada.

>[!NOTE]
>Você pode usar a janela **imediata** em tempo de design com a maioria dos tipos de projeto. Não há suporte para SQL, projetos Web ou script.

Por exemplo, para testar um método chamado `Test` na classe `Class1` :

1. Com o projeto da dll aberto, abra a janela **imediata** selecionando **depurar**  >  **janelas**  >  **imediatamente** ou pressionando **Ctrl** + **ALT** + **I**.

1. Crie uma instância de um objeto do tipo `Class1` digitando o seguinte código C# na janela **imediata** e pressionando **Enter**. Esse código gerenciado funciona para C# e Visual Basic, com as alterações de sintaxe apropriadas:

   ```csharp
   Class1 obj = new Class1();
   ```

   No C#, todos os nomes devem ser totalmente qualificados. Quaisquer métodos ou variáveis devem estar no escopo atual e no contexto quando o serviço de linguagem tentar avaliar a expressão.

1. Supondo que `Test` aceite um parâmetro `int`, avalie `Test` usando a janela **Imediato**:

   ```csharp
   ?obj.Test(10);
   ```

   O resultado é impresso na janela **imediata** .

1. Você pode continuar a depuração do `Test` colocando um ponto de interrupção dentro dele e avaliando a função novamente.

   O ponto de interrupção será atingido e você poderá percorrer `Test` . Após a execução do `Test`, o Depurador voltará ao modo Design.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Depuração de modo misto

Você pode escrever um aplicativo de chamada para uma DLL em código gerenciado ou nativo. Se seu aplicativo nativo chama uma DLL gerenciada e você deseja depurar ambos, você pode habilitar os depuradores gerenciados e nativos nas propriedades do projeto. O processo exato depende se você deseja iniciar a depuração do projeto de DLL ou o projeto de aplicativo de chamada. Para obter mais informações, consulte [como depurar em modo misto](../debugger/how-to-debug-in-mixed-mode.md).

Você também pode depurar uma DLL nativa de um projeto de chamada gerenciado. Para obter mais informações, consulte [como depurar código gerenciado e nativo](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Consulte também
- [Depurar o código gerenciado](../debugger/debugging-managed-code.md)
- [Preparar para depurar projetos C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipos de projeto C#, F # e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Configurações do projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configurações de projeto para configurações de depuração em C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configurações de projeto para uma configuração de depuração de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Segurança do depurador](../debugger/debugger-security.md)
