---
title: Ampliando a barra de status | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711540"
---
# <a name="extend-the-status-bar"></a>Estender a barra de status
Você pode usar a barra de status do Visual Studio na parte inferior do IDE para exibir informações.

 Quando você estende a barra de status, você pode exibir informações e iU em quatro regiões: a região de feedback, a barra de progresso, a região de animação e a região do designer. A região de feedback permite que você exiba texto e destaque o texto exibido. A barra de progresso mostra progresso incremental para operações de curto prazo, como salvar um arquivo. A região de animação exibe uma animação em loop contínuo para operações de longa duração ou operação de comprimento indeterminado, como a construção de vários projetos em uma solução. E a região do designer mostra o número da linha e da coluna do local do cursor.

 Você pode obter a barra <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> de status <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> usando a interface (do serviço). Além disso, qualquer objeto situado em um quadro de janela pode <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> registrar-se como um objeto cliente da barra de status implementando a interface. Sempre que uma janela é ativada, o Visual Studio `IVsStatusbarUser` consulta o objeto situado naquela janela para a interface. Se encontrado, ele <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> chama o método na interface retornada e o objeto pode atualizar a barra de status dentro desse método. Janelas de documentos, por <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> exemplo, podem usar o método para atualizar informações na região do designer quando elas se tornarem ativas.

 Os procedimentos a seguir assumem que você entende como criar um projeto VSIX e adicionar um comando de menu personalizado. Para obter informações, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modificar a barra de status
 Este procedimento mostra como definir e obter texto, exibir texto estático e destacar o texto exibido na região de feedback da barra de status.

### <a name="read-and-write-to-the-status-bar"></a>Ler e escrever na barra de status

1. Crie um projeto VSIX chamado **TestStatusBarExtension** e adicione um comando de menu chamado **TestStatusBarCommand**.

2. Em *TestStatusBarCommand.cs,* substitua o`MenuItemCallback`código do método do manipulador de comandos ( ) pelo seguinte:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Compile o código e comece a depurar.

4. Abra o menu **Ferramentas** na instância experimental do Visual Studio. Clique no botão **Invocar TestStatusBarCommand.**

     Você deve ver que o texto na barra de status agora lê **Que acabamos de escrever para a barra de status.** e a caixa de mensagens que aparece tem o mesmo texto.

### <a name="update-the-progress-bar"></a>Atualize a barra de progresso

1. Neste procedimento mostraremos como inicializar e atualizar a barra de progresso.

2. Abra *TestStatusBarCommand.cs* o arquivo TestStatusBarCommand.cs `MenuItemCallback` e substitua o método pelo seguinte código:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Compile o código e comece a depurar.

4. Abra o menu **Ferramentas** na instância experimental do Visual Studio. Clique em Invocar o botão **TestStatusBarCommand.**

     Você deve ver que o texto na barra de status agora lê **Escrever para a barra de progresso.** Você também deve ver a barra de progresso ser atualizada a cada segundo durante 20 segundos. Depois disso, a barra de status e a barra de progresso são liberadas.

### <a name="display-an-animation"></a>Exibir uma animação

1. A barra de status exibe uma animação de looping que indica uma operação de longa duração (por exemplo, construir vários projetos em uma solução). Se você não ver esta animação, certifique-se de ter as configurações corretas > **de opções de** **ferramentas:**

     Vá para a guia **Ferramentas** > **Opções** > **Gerais** e desfaça a **verificação automaticamente ajuste a experiência visual com base no desempenho do cliente**. Em seguida, verifique a subopção **Habilitar a experiência visual do cliente rico**. Agora você deve ser capaz de ver a animação quando você construir o projeto em sua instância experimental do Visual Studio.

     Neste procedimento, exibimos a animação padrão do Visual Studio que representa a construção de um projeto ou solução.

2. Abra *TestStatusBarCommand.cs* o arquivo TestStatusBarCommand.cs `MenuItemCallback` e substitua o método pelo seguinte código:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Compile o código e comece a depurar.

4. Abra o menu **Ferramentas** na instância experimental do Visual Studio e clique **em Invocar TestStatusBarCommand**.

     Quando você vê a caixa de mensagens, você também deve ver a animação na barra de status na extrema direita. Quando você descarta a caixa de mensagens, a animação desaparece.
