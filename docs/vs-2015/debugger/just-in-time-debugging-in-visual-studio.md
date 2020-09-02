---
title: Depuração Just-In-Time
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690602"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Depuração Just-In-Time no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A depuração Just-in-time inicia o Visual Studio automaticamente quando ocorre uma exceção ou uma falha em um aplicativo que está sendo executado fora do Visual Studio. Isso permite testar seu aplicativo quando o Visual Studio não está em execução e começar a depuração com o Visual Studio quando ocorrer um problema.

A depuração Just-in-time funciona para aplicativos da área de trabalho do Windows. Ele não funciona para aplicativos universais do Windows e não funciona para código gerenciado hospedado em um aplicativo nativo, como visualizadores.

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> A caixa de diálogo do depurador just-in-time aparece ao tentar executar um aplicativo?

As ações que você deve executar quando vir a caixa de diálogo do depurador just-in-time do Visual Studio dependem do que você está tentando fazer:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Se você quiser se livrar da caixa de diálogo e simplesmente executar o aplicativo normalmente

1. (Usuários avançados) Se você tiver instalado o Visual Studio (ou se o tiver instalado anteriormente e removido), [desabilite a depuração Just-in-time](#BKMK_Enabling) e tente executar o aplicativo novamente.

2. Se você estiver executando um aplicativo Web no Internet Explorer, desabilite a depuração de script.

    Desabilite a depuração de script na caixa de diálogo Opções da Internet. Você pode acessá-lo nas opções de rede do **painel de controle**  /  **e**  /  **Internet** da Internet (as etapas exatas dependem da sua versão do Windows e do Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Abra novamente a página da Web onde você encontrou o erro. Se isso não resolver o problema, entre em contato com o proprietário do aplicativo Web para corrigir o problema.

4. Se você estiver executando outro tipo de aplicativo do Windows, será necessário entrar em contato com o proprietário do aplicativo para corrigir o erro e reinstalar a versão fixa do aplicativo.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Se você quiser corrigir ou depurar o erro (usuários avançados)

- Você deve ter o [Visual Studio instalado](https://visualstudio.microsoft.com/vs/older-downloads/) para exibir as informações detalhadas sobre o erro e tentar depurá-lo. Consulte [usando o JIT](#BKMK_Using_JIT) para obter instruções detalhadas. Se você não puder resolver o erro e corrigir o aplicativo, entre em contato com o proprietário do aplicativo para resolver o erro.

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> Habilitar ou desabilitar a depuração Just-in-time
 Você pode habilitar ou desabilitar a depuração Just-in-time na caixa de diálogo **ferramentas/opções** do Visual Studio.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Para habilitar ou desabilitar a depuração Just-In-Time

1. Abra o Visual Studio. No menu **Ferramentas** , clique em **Opções**.

2. Na caixa de diálogo **Opções** , selecione a pasta **depuração** .

3. Na pasta **depuração** , selecione a página **just-in-time** .

4. Na caixa de seleção **Habilitar depuração Just-in-time desses tipos de código** , marque ou desmarque os tipos de programa relevantes: **gerenciado**, **nativo**ou **script**.

    Para desabilitar a depuração Just-In-Time depois que ela tiver sido habilitada, você deve executar com privilégios de administrador. A habilitação da depuração Just-In-Time define uma chave do Registro, sendo necessários privilégios de Administrador para alterar essa chave.

5. Clique em **OK**.

   A depuração Just-In-Time ainda poderá ser habilitada, mesmo que o Visual Studio não esteja mais instalado no seu computador. Quando o Visual Studio não está instalado, não é possível desabilitar a depuração Just-in-time na caixa de diálogo **Opções** do Visual Studio. Nesse caso, você poderá desabilitar a depuração Just-In-Time editando o Registro do Windows.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Para desabilitar a depuração Just-In-Time editando o Registro

1. No menu **Iniciar** , pesquise e execute `regedit.exe`

2. Na janela **Editor do registro** , localize e exclua as seguintes entradas do registro:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3. Se o computador estiver executando um sistema operacional de 64 bits, exclua as seguintes entradas de registro também:

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4. Tenha cuidado para não excluir ou não alterar acidentalmente quaisquer outras chaves do Registro.

5. Feche a janela **Editor do Registro**.

> [!NOTE]
> Se você estiver tentando desabilitar a depuração Just-in-time para um aplicativo do lado do servidor e essas etapas não resolverem o problema, desative a depuração do lado do servidor nas configurações do aplicativo IIS e tente novamente.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Para habilitar a depuração Just-In-Time de um formulário do Windows

1. Por padrão, os aplicativos do Windows Forms têm um manipulador de exceção de nível superior que permite que o programa continue a executar se puder recuperar. Por exemplo, se seu aplicativo de Windows Forms lançar uma exceção sem tratamento, você verá uma caixa de diálogo semelhante à seguinte:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Para habilitar a depuração Just-in-time de um aplicativo Windows Forms, você deve executar as seguintes etapas adicionais:

2. Defina o `jitDebugging` valor como `true` na `system.windows.form` seção do arquivo de machine.config ou *\<application name>*.exe.config:

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. No aplicativo C++ do Windows Form, você também deve definir `DebuggableAttribute` em um arquivo .config ou no seu código. Se você compilar com [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) e sem [/Og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), o compilador definirá esse atributo para você. Se você desejar depurar uma compilação de liberação não otimizada, no entanto, deverá definir isso por conta própria. Você pode fazer isso adicionando a seguinte linha ao arquivo de AssemblyInfo.cpp do seu aplicativo:

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Para obter mais informações, consulte <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Usar depuração Just-in-time
 Esta seção mostra o que acontece quando um executável gera uma exceção.

 Você deve ter o Visual Studio instalado para seguir estas etapas. Se você não tiver o Visual Studio, poderá baixar o [visual studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/)gratuito.

 Quando você instala o Visual Studio, a depuração Just-In-Time é habilitada por padrão.

 Para os fins desta seção, vamos criar um aplicativo de console em C# no Visual Studio que lança um <xref:System.NullReferenceException> .

 No Visual Studio, crie um aplicativo de console em C# (**arquivo/novo/projeto/Visual C#/aplicativo de console**) chamado **ThrowsNullException**. Para obter mais informações sobre como criar projetos no Visual Studio, consulte [passo a passos: criar um aplicativo simples](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Quando o projeto for aberto no Visual Studio, abra o arquivo Program.cs. Substitua o método Main () pelo código a seguir, que imprime uma linha no console e, em seguida, gera uma NullReferenceException:

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> Para que esse procedimento funcione em uma configuração de [versão](../debugger/how-to-set-debug-and-release-configurations.md), você precisa desativar [apenas meu código](../debugger/just-my-code.md). No Visual Studio, clique em **ferramentas/opções**. Na caixa de diálogo **Opções** , selecione **depuração**. Remova a marca de seleção **habilitar apenas meu código**.

 Compile a solução (no Visual Studio, escolha **Compilar/recompilar solução**). Você pode escolher a configuração de depuração ou de versão. Para obter mais informações sobre configurações de compilação, consulte [noções básicas sobre configurações de compilação](../ide/understanding-build-configurations.md).

 O processo de compilação cria um ThrowsNullException.exe executável. Você pode encontrá-lo na pasta em que você criou o projeto C#: **. ..\ThrowsNullException\ThrowsNullException\bin\Debug** ou **. ..\ThrowsNullException\ThrowsNullException\bin\Release**.

 Clique duas vezes no ThrowsNullException.exe. Você deverá ver uma janela de comando como esta:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Depois de alguns segundos, uma janela de erro é exibida:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Não clique em **Cancelar**! Após alguns segundos, você deverá ver dois botões, **depurar** e **fechar programa**. Clique em **depurar**.

> [!CAUTION]
> Se seu aplicativo contiver código não confiável, será exibida uma caixa de diálogo com um aviso de segurança. Essa caixa de diálogo permite que você decida se deseja continuar com a depuração. Antes de prosseguir com a depuração, decida se você confia no código. Você mesmo escreveu o código? Você confia no programador? Se o aplicativo está sendo executado em um computador remoto, você reconhece o nome do processo? Mesmo que o aplicativo seja executado localmente, isso não significa necessariamente que ele é confiável. Considere a possibilidade de código mal-intencionado em execução no seu computador. Se você decidir que o código que está prestes a depurar é confiável, clique em **depurar**. Caso contrário, clique em **não depurar**.

 A janela do **depurador just-in-time do Visual Studio** é exibida:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 Em **possíveis depuradores**, você verá que a **nova instância do Microsoft Visual Studio linha 2015** está selecionada. Se ele ainda não estiver selecionado, selecione-o agora.

 Na parte inferior da janela, em **deseja depurar usando o depurador selecionado?**, clique em **Sim**.

 O projeto ThrowsNullException é aberto em uma nova instância do Visual Studio, com a execução interrompida na linha que gera a exceção:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Você pode iniciar a depuração neste ponto. Se esse fosse um aplicativo real, você precisaria descobrir por que o código está lançando a exceção.

## <a name="just-in-time-debugging-errors"></a>Erros da depuração Just-In-Time
 Se você não vir a caixa de diálogo quando o programa falhar, isso pode ser devido a Relatório de Erros do Windows configurações em seu computador. Para obter mais informações, consulte [. Configurações do WER](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Você pode ver as seguintes mensagens de erro que estão associadas à depuração Just-In-Time.

- **Não é possível anexar ao processo de falha. O programa especificado não é um programa do Windows ou MS-DOS.**

     Esse erro ocorre quando você tenta anexar a um processo em execução como outro usuário.

     Para contornar esse problema, inicie o Visual Studio, abra a caixa de diálogo **anexar ao processo** no menu **depurar** e localize o processo que você deseja depurar na lista **processos disponíveis** . Se você não souber o nome do processo, examine a caixa de diálogo do **depurador just-in-time do Visual Studio** e anote a ID do processo. Selecione o processo na lista **processos disponíveis** e clique em **anexar**. No diálogo **depurador just-in-time do Visual Studio** , clique em **não** para ignorar a caixa de diálogo.

- **Não foi possível iniciar o depurador porque não há usuário conectado.**

     Este erro ocorre quando a depuração Just-In-Time tenta iniciar o Visual Studio em um computador no qual não há nenhum usuário conectado ao console. Como nenhum usuário está conectado, não há sessão de usuário para exibir a caixa de diálogo Depuração Just-In-Time.

     Para corrigir esse problema, conecte-se ao computador.

- **Classe não registrada.**

     Este erro indica que o depurador tentou criar uma classe COM não registrada, provavelmente devido a um problema de instalação.

     Para corrigir o problema, use o disco de instalação para reinstalar ou reparar sua instalação do Visual Studio.

## <a name="see-also"></a>Consulte Também
 [Debugger Security](../debugger/debugger-security.md) [Noções básicas do depurador](../debugger/debugger-basics.md) de segurança [do depurador, logons, depuração, opções caixa de diálogo opção](../debugger/just-in-time-debugging-options-dialog-box.md) de [segurança AVISO: anexar a um processo de propriedade de um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou se você não tiver certeza, não anexe a este processo](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)
