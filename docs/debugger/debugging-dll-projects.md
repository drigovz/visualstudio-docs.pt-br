---
title: Projetos de Debug DLL | Microsoft Docs
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
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302199"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Debug DLLs in Visual Studio (C#, C++, Visual Basic, F#)

Uma DLL (biblioteca de link dinâmico) é uma biblioteca que contém código e dados que podem ser usados por mais de um aplicativo. Você pode usar o Visual Studio para criar, construir, configurar e depurar DLLs.

## <a name="create-a-dll"></a>Criar um DLL

Os seguintes modelos de projeto do Visual Studio podem criar DLLs:

- C#, Visual Basic ou F# Class Library
- C# ou Biblioteca de Controle de Formulários Básicos Visuais do Windows (WCF)
- C++ Biblioteca de Link Dinâmico (DLL)

Para obter mais informações, consulte [as técnicas de depuração do MFC](../debugger/mfc-debugging-techniques.md).

Depurar uma Biblioteca WCF é semelhante à depuração de uma Biblioteca de Classes. Para obter detalhes, consulte [Controles de formulários do Windows](/dotnet/framework/winforms/controls/index).

Você geralmente chama um DLL de outro projeto. Quando você depura o projeto de chamada, dependendo da configuração de DLL, você pode entrar e depurar o código DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Configuração de depuração de DLL

Quando você usa um modelo de projeto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do Visual Studio para criar um aplicativo, cria automaticamente as configurações necessárias para configurações de compilação Debug e Release. Você pode alterar essas configurações se necessário. Para obter mais informações, consulte os seguintes artigos:

- [Configurações do projeto para uma configuração de depuração C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configurações do projeto para configurações de depuração C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Como: Definir configurações de depuração e lançamento](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Definir C++ DepuravelAttributea

Para que o depurador seja anexado a uma DLL C++, o código C++ deve ser emitido `DebuggableAttribute`.

**Para `DebuggableAttribute`definir:**

1. Selecione o projeto C++ DLL no **Solution Explorer** e selecione o ícone **Propriedades** ou clique com o botão direito do mouse no projeto e selecione **Propriedades**.

1. No painel **Propriedades,** em**Depuração** **de Linker,** > selecione **Sim (/ASSEMBLYDEBUG)** para **Conjunto Depurado**.

Para obter mais informações, consulte [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a>Definir os locais do arquivo C/C++ DLL

Para depurar um DLL externo, um projeto de chamada deve ser capaz de encontrar o DLL, seu [arquivo .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e quaisquer outros arquivos que o DLL exija. Você pode criar uma tarefa de compilação personalizada para copiar esses arquivos para a * \<pasta de projeto>\Depuração* pasta de saída, ou você pode copiar os arquivos lá manualmente.

Para projetos C/C++, você pode definir os locais de cabeçalho e arquivo LIB nas páginas de propriedade do projeto, em vez de copiá-los para a pasta de saída.

**Para definir o cabeçalho C/C++ e os locais do arquivo LIB:**

1. Selecione o projeto C/C++ DLL no **Solution Explorer** e selecione o ícone **Propriedades** ou clique com o botão direito do mouse no projeto e selecione **Propriedades**.

1. Na parte superior do painel **Propriedades,** em **Configuração,** selecione **Todas as configurações**.

1. Em **C/C++** > **Diretórios adicionais adicionais,** > **Additional Include Directories**especifique a pasta que tem arquivos de cabeçalho.

1. Em Diretórios**de** > **bibliotecas adicionais adicionais do** **Linker** > General, especifique a pasta que tem arquivos LIB.

1. Em **Linker** > **Input** > Adicional**Dependencies**, especifique o caminho completo e o nome do arquivo para os arquivos LIB.

1. Selecione **OK**.

Para obter mais informações sobre as configurações do projeto C++, consulte [a referência da página de propriedade do Windows C++.](/cpp/build/reference/property-pages-visual-cpp)

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Construa uma versão de depuração

Certifique-se de construir uma versão Debug do DLL antes de começar a depurar. Para depurar um DLL, um aplicativo de chamada deve ser capaz de encontrar seu [arquivo .pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e quaisquer outros arquivos que a DLL exija.

Você pode criar uma tarefa de compilação personalizada para copiar os arquivos DLL para a * \<pasta de projeto de chamada>\Depuração* pasta de saída, ou você pode copiar os arquivos lá manualmente.

Certifique-se de ligar para a DLL em sua localização correta. Isso pode parecer óbvio, mas se um aplicativo de chamada encontrar e carregar uma cópia diferente da DLL, o depurador nunca atingirá os pontos de interrupção definidos.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Depurar um DLL

Você não pode executar um DLL diretamente. Ele deve ser chamado por um aplicativo, geralmente um arquivo *.exe.* Para obter mais informações, consulte [projetos do Visual Studio - C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Para depurar um DLL, você pode [começar a depurar a partir do aplicativo de chamada](#vxtskdebuggingdllprojectsthecallingapplication)ou [depurar do projeto DLL](how-to-debug-from-a-dll-project.md) especificando seu aplicativo de chamada. Você também pode usar a janela dedepuração [Imediata](#vxtskdebuggingdllprojectstheimmediatewindow) para avaliar funções ou métodos de DLL na hora do projeto, sem usar um aplicativo de chamada.

Para obter mais informações, consulte [Primeiro olhar para o depurador](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Comece a depurar a partir do aplicativo de chamada

O aplicativo que chama uma DLL pode ser:

- Um aplicativo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de um projeto na mesma ou uma solução diferente da DLL.
- Um aplicativo existente que já está implantado e em execução em um computador de teste ou produção.
- Localizado na Web e acessado por meio de uma URL.
- Um aplicativo web com uma página web que incorpora o DLL.

Para depurar um DLL de um aplicativo de chamada, você pode:

- Abra o projeto para o aplicativo de chamada e inicie a depuração selecionando **Debug** > **Start Debugging** ou pressionando **F5**.

  ou

- Conecte-se a um aplicativo que já está implantado e em execução em um computador de teste ou produção. Use este método para DLLs em sites ou em aplicativos web. Para obter mais informações, consulte [Como: Anexar a um processo em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Antes de começar a depurar o aplicativo de chamada, defina um ponto de ruptura na DLL. Consulte [Usando pontos de interrupção](../debugger/using-breakpoints.md). Quando o ponto de ruptura dll é atingido, você pode passar pelo código, observando a ação em cada linha. Para obter mais informações, consulte [Navegar código no depurador](../debugger/navigating-through-code-with-the-debugger.md).

Durante a depuração, você pode usar a janela **Módulos** para verificar os Arquivos DLLs e *.exe* que o aplicativo carrega. Para abrir a janela **Módulos,** durante a depuração, selecione **Depurar** > **módulos do****Windows** > . Para obter mais informações, [consulte Como: Usar a janela Módulos](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Use a janela Imediata

Você pode usar a janela **Imediata** para avaliar funções ou métodos de DLL no momento do projeto. A janela **Immediate** desempenha o papel de um aplicativo de chamada.

>[!NOTE]
>Você pode usar a janela **Imediato** na hora do projeto com a maioria dos tipos de projeto. Não é suportado para SQL, projetos web ou script.

Por exemplo, para testar `Test` um `Class1`método nomeado na classe:

1. Com o projeto DLL aberto, abra a janela **Imediato** selecionando **Debug** > **Windows** > **Immediate** ou pressionando **Ctrl**+**Alt**+**I**.

1. Instanciar um `Class1` objeto de tipo digitando o seguinte código C# na janela **Imediata** e pressionando **Enter**. Este código gerenciado funciona para C# e Visual Basic, com alterações de sintaxe apropriadas:

   ```csharp
   Class1 obj = new Class1();
   ```

   No C#, todos os nomes devem ser totalmente qualificados. Quaisquer métodos ou variáveis devem estar no escopo e contexto atuais quando o serviço de linguagem tenta avaliar a expressão.

1. Supondo que `Test` aceite um parâmetro `int`, avalie `Test` usando a janela **Imediato**:

   ```csharp
   ?obj.Test(10);
   ```

   O resultado é impresso na janela **Imediata.**

1. Você pode continuar a depuração do `Test` colocando um ponto de interrupção dentro dele e avaliando a função novamente.

   O ponto de ruptura será atingido, `Test`e você pode passar. Após a execução do `Test`, o Depurador voltará ao modo Design.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>Depuração de modo misto

Você pode escrever um aplicativo de chamada para um DLL em código gerenciado ou nativo. Se o aplicativo nativo chamar uma DLL gerenciada e você quiser depurar ambos, você poderá habilitar os depuradores gerenciados e nativos nas propriedades do projeto. O processo exato depende se você deseja começar a depurar a partir do projeto DLL ou do projeto do aplicativo de chamada. Para obter mais informações, consulte [Como: Depurar no modo misto](../debugger/how-to-debug-in-mixed-mode.md).

Você também pode depurar um DLL nativo de um projeto de chamada gerenciado. Para obter mais informações, consulte [Como depurar código gerenciado e nativo](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Confira também
- [Depurar o código gerenciado](../debugger/debugging-managed-code.md)
- [Prepare-se para depurar projetos C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipos de projeto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Configurações do projeto para uma configuração C++ Debug](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configurações do projeto para configurações c# debug](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configurações do projeto para uma configuração de depuração básica visual](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Segurança do depurador](../debugger/debugger-security.md)
