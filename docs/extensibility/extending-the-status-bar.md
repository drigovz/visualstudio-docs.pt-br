---
title: Estendendo a barra de status | Microsoft Docs
description: Saiba como estender a barra de status do Visual Studio na parte inferior do IDE, que exibe informações.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7776c7fa35cd7ac06dec60ced3604cb67c96da4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903192"
---
# <a name="extend-the-status-bar"></a>Estender a barra de status
Você pode usar a barra de status do Visual Studio na parte inferior do IDE para exibir informações.

 Ao estender a barra de status, você pode exibir informações e a interface do usuário em quatro regiões: a região de comentários, a barra de progresso, a região de animação e a região do designer. A região de comentários permite exibir texto e realçar o texto exibido. A barra de progresso mostra o progresso incremental para operações de execução curta, como salvar um arquivo. A região de animação exibe uma animação em loop contínuo para operações de longa execução ou operação de comprimento indeterminado, como a criação de vários projetos em uma solução. E a região do designer mostra o número da linha e da coluna do local do cursor.

 Você pode obter a barra de status usando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interface (do <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> serviço). Além disso, qualquer objeto de site em um quadro de janela pode ser registrado como um objeto de cliente de barra de status implementando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interface. Sempre que uma janela é ativada, o Visual Studio consulta o objeto site na janela para a `IVsStatusbarUser` interface. Se for encontrado, ele chamará o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método na interface retornada e o objeto poderá atualizar a barra de status dentro desse método. As janelas de documentos, por exemplo, podem usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método para atualizar as informações na região do designer quando elas se tornam ativas.

 Os procedimentos a seguir pressupõem que você entenda como criar um projeto VSIX e adicionar um comando de menu personalizado. Para obter informações, consulte [criar uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modificar a barra de status
 Este procedimento mostra como definir e obter texto, exibir texto estático e realçar o texto exibido na região de comentários da barra de status.

### <a name="read-and-write-to-the-status-bar"></a>Ler e gravar na barra de status

1. Crie um projeto VSIX chamado **TestStatusBarExtension** e adicione um comando de menu chamado **TestStatusBarCommand**.

2. No *TestStatusBarCommand.cs*, substitua o código do método do manipulador de comandos ( `MenuItemCallback` ) pelo seguinte:

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

3. Compile o código e inicie a depuração.

4. Abra o menu **ferramentas** na instância experimental do Visual Studio. Clique no botão **invocar TestStatusBarCommand** .

     Você deve ver que o texto na barra de status agora lê que **acabamos de gravar na barra de status.** e a caixa de mensagem que aparece tem o mesmo texto.

### <a name="update-the-progress-bar"></a>Atualizar a barra de progresso

1. Neste procedimento, mostraremos como inicializar e atualizar a barra de progresso.

2. Abra o arquivo *TestStatusBarCommand.cs* e substitua o `MenuItemCallback` método pelo código a seguir:

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

3. Compile o código e inicie a depuração.

4. Abra o menu **ferramentas** na instância experimental do Visual Studio. Clique no botão **invocar TestStatusBarCommand** .

     Você deve ver que o texto na barra de status agora lê **gravando na barra de progresso.** Você também deve ver a barra de progresso ser atualizada a cada segundo por 20 segundos. Depois que a barra de status e a barra de progresso são limpas.

### <a name="display-an-animation"></a>Exibir uma animação

1. A barra de status exibe uma animação de loop que indica uma operação de execução longa (por exemplo, a criação de vários projetos em uma solução). Se você não vir essa animação, certifique-se de ter as configurações corretas  >  das **Opções** de ferramentas:

     Vá para a guia **ferramentas**  >  **Opções**  >  **geral** e desmarque a opção **ajustar automaticamente a experiência visual com base no desempenho do cliente**. Em seguida, marque a subopção **habilitar experiência visual de cliente avançada**. Agora você deve ser capaz de ver a animação ao compilar o projeto em sua instância experimental do Visual Studio.

     Neste procedimento, exibimos a animação padrão do Visual Studio que representa a criação de um projeto ou uma solução.

2. Abra o arquivo *TestStatusBarCommand.cs* e substitua o `MenuItemCallback` método pelo código a seguir:

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

3. Compile o código e inicie a depuração.

4. Abra o menu **ferramentas** na instância experimental do Visual Studio e clique em **invocar TestStatusBarCommand**.

     Quando você vir a caixa de mensagem, você também deverá ver a animação na barra de status na extrema direita. Quando você descarta a caixa de mensagem, a animação desaparece.
