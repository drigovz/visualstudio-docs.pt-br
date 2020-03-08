---
title: Depurar projetos DLL | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409384"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Depurar DLLs no Visual Studio (C#, C++, Visual Basic, F#)

Uma DLL (biblioteca de vínculo dinâmico) é uma biblioteca que contém código e dados que podem ser usados por mais de um aplicativo. Você pode usar o Visual Studio para criar, compilar, configurar e depurar DLLs.

## <a name="create-a-dll"></a>Criar uma DLL

Os seguintes modelos de projeto do Visual Studio podem criar DLLs:

- C#, Visual Basic ou F# biblioteca de classes
- C#ou Visual Basic biblioteca de controle de Windows Forms (WCF)
- C++Biblioteca de vínculo dinâmico (DLL)

Para obter mais informações, consulte [técnicas de depuração do MFC](../debugger/mfc-debugging-techniques.md).

A depuração de uma biblioteca WCF é semelhante à depuração de uma biblioteca de classes. Para obter detalhes, consulte [controles de Windows Forms](/dotnet/framework/winforms/controls/index).

Normalmente, você chama uma DLL de outro projeto. Ao depurar o projeto de chamada, dependendo da configuração de DLL, você pode entrar e depurar o código de DLL.

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Configuração de depuração de DLL

Quando você usa um modelo de projeto do Visual Studio para criar um aplicativo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria automaticamente as configurações necessárias para depurar e liberar as configurações de compilação. Você pode alterar essas configurações, se necessário. Para obter mais informações, confira os seguintes artigos:

- [Configurações do projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Configurações do projeto para configurações de depuração do C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Como definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Definir C++ DebuggableAttribute

Para que o depurador seja anexado a C++ uma dll, C++ o código deve emitir `DebuggableAttribute`.

**Para definir `DebuggableAttribute`:**

1. Selecione o C++ projeto de DLL no **Gerenciador de soluções** , selecione o ícone **Propriedades** ou clique com o botão direito do mouse no projeto e selecione **Propriedades**.

1. No painel **Propriedades** , em **vinculador** > **depuração**, selecione **Sim (/ASSEMBLYDEBUG)** para o **assembly depurável**.

Para obter mais informações, consulte [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="vxtskdebuggingdllprojectsexternal"></a>Definir locais deC++ arquivo C/DLL

Para depurar uma DLL externa, um projeto de chamada deve ser capaz de localizar a DLL, seu [arquivo. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e todos os outros arquivos necessários para a dll. Você pode criar uma tarefa de compilação personalizada para copiar esses arquivos para a *pasta\<projeto >* pasta de saída \debug ou pode copiar os arquivos manualmente.

Para C/C++ Projects, você pode definir os locais de arquivo de cabeçalho e lib nas páginas de propriedades do projeto, em vez de copiá-los para a pasta de saída.

**Para definir os locaisC++ do arquivo C/Header e lib:**

1. Selecione o projeto CC++ /DLL no **Gerenciador de soluções** , selecione o ícone **Propriedades** ou clique com o botão direito do mouse no projeto e selecione **Propriedades**.

1. Na parte superior do painel **Propriedades** , em **configuração**, selecione **todas as configurações**.

1. Em **C/C++**  > **geral** > **diretórios de inclusão adicionais**, especifique a pasta que tem os arquivos de cabeçalho.

1. Em **vinculador** > **geral** > **diretórios de bibliotecas adicionais**, especifique a pasta que tem os arquivos lib.

1. Em **vinculador** > **entrada** > **dependências adicionais**, especifique o caminho completo e o nome do arquivo para os arquivos lib.

1. Selecione **OK**.

Para obter mais informações C++ sobre as configurações do projeto, consulte [referência da página de C++ Propriedades do Windows](/cpp/build/reference/property-pages-visual-cpp).

## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Compilar uma versão de depuração

Certifique-se de criar uma versão de depuração da DLL antes de iniciar a depuração. Para depurar uma DLL, um aplicativo de chamada deve ser capaz de encontrar seu [arquivo. pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e quaisquer outros arquivos necessários para a dll.

Você pode criar uma tarefa de compilação personalizada para copiar os arquivos DLL para o *\<a pasta de projeto de chamada >* pasta de saída \debug ou pode copiar os arquivos manualmente.

Certifique-se de chamar a DLL em seu local correto. Isso pode parecer óbvio, mas se um aplicativo de chamada encontrar e carregar uma cópia diferente da DLL, o depurador nunca atingirá os pontos de interrupção que você definir.

## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Depurar uma DLL

Você não pode executar uma DLL diretamente. Ele deve ser chamado por um aplicativo, geralmente um arquivo *. exe* . Para obter mais informações, consulte [projetos do Visual C++Studio- ](/cpp/ide/creating-and-managing-visual-cpp-projects).

Para depurar uma DLL, você pode [iniciar a depuração do aplicativo de chamada](#vxtskdebuggingdllprojectsthecallingapplication)ou [depurar a partir do projeto de dll](how-to-debug-from-a-dll-project.md) especificando seu aplicativo de chamada. Você também pode usar a janela do depurador [imediato](#vxtskdebuggingdllprojectstheimmediatewindow) para avaliar funções ou métodos de dll em tempo de design, sem usar um aplicativo de chamada.

Para obter mais informações, consulte [primeira olhada no depurador](../debugger/debugger-feature-tour.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Iniciar a depuração do aplicativo de chamada

O aplicativo que chama uma DLL pode ser:

- Um aplicativo de um projeto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no mesmo ou em uma solução diferente da DLL.
- Um aplicativo existente que já está implantado e em execução em um computador de teste ou de produção.
- Localizado na Web e acessado por meio de uma URL.
- Um aplicativo Web com uma página da Web que incorpora a DLL.

Para depurar uma DLL de um aplicativo de chamada, você pode:

- Abra o projeto para o aplicativo de chamada e inicie a depuração selecionando **Debug** > **iniciar a depuração** ou pressionar **F5**.

  ou

- Anexe a um aplicativo que já está implantado e em execução em um computador de teste ou de produção. Use esse método para DLLs em sites ou em aplicativos Web. Para obter mais informações, consulte [como: anexar a um processo em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Antes de iniciar a depuração do aplicativo de chamada, defina um ponto de interrupção na DLL. Consulte [usando pontos de interrupção](../debugger/using-breakpoints.md). Quando o ponto de interrupção da DLL é atingido, você pode percorrer o código, observando a ação em cada linha. Para obter mais informações, consulte [navegar no código no depurador](../debugger/navigating-through-code-with-the-debugger.md).

Durante a depuração, você pode usar a janela **módulos** para verificar os arquivos DLLs e *. exe* que o aplicativo carrega. Para abrir a janela **módulos** , durante a depuração, selecione **depurar** > **módulos**de > do **Windows** . Para obter mais informações, consulte [como: usar a janela módulos](../debugger/how-to-use-the-modules-window.md).

### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Usar a janela imediata

Você pode usar a janela **imediata** para avaliar funções de dll ou métodos em tempo de design. A janela **imediata** desempenha a função de um aplicativo de chamada.

>[!NOTE]
>Você pode usar a janela **imediata** em tempo de design com a maioria dos tipos de projeto. Não há suporte para SQL, projetos Web ou script.

Por exemplo, para testar um método chamado `Test` na classe `Class1`:

1. Com o projeto da DLL aberto, abra a janela **imediata** selecionando **depurar** > o **Windows** > **imediato** ou pressionando **Ctrl**+**ALT**+**I**.

1. Crie uma instância de um objeto do tipo `Class1` digitando o código a seguir C# na janela **imediata** e pressionando **Enter**. Esse código gerenciado funciona para C# o e o Visual Basic, com as alterações de sintaxe apropriadas:

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

   O ponto de interrupção será atingido e você poderá percorrer `Test`. Após a execução do `Test`, o Depurador voltará ao modo Design.

## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Depuração de modo misto

Você pode escrever um aplicativo de chamada para uma DLL em código gerenciado ou nativo. Se seu aplicativo nativo chama uma DLL gerenciada e você deseja depurar ambos, você pode habilitar os depuradores gerenciados e nativos nas propriedades do projeto. O processo exato depende se você deseja iniciar a depuração do projeto de DLL ou o projeto de aplicativo de chamada. Para obter mais informações, consulte [como depurar em modo misto](../debugger/how-to-debug-in-mixed-mode.md).

Você também pode depurar uma DLL nativa de um projeto de chamada gerenciado. Para obter mais informações, consulte [como depurar código gerenciado e nativo](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Consulte também
- [Depurar código gerenciado](../debugger/debugging-managed-code.md)
- [Preparar para depurar C++ projetos](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipos de projeto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Definições do projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Definições do projeto para configurações de depuração do C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Definições do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Segurança do depurador](../debugger/debugger-security.md)
