---
title: 'Walkthrough: Depurando um Windows Form | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a553f77e352b16ba1a0709e13e8893cf0f57a43d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704906"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Passo a passo: Depurando um Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um Windows Form é um dos aplicativos gerenciados mais comuns. Um Windows Form cria um aplicativo padrão do Windows. Você pode concluir este passo a passo usando o Visual Basic, C# ou C++.  
  
 Primeiro, você deve fechar as soluções abertas.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Para preparar-se para esse passo a passo  
  
- Se você já tiver uma solução aberta, feche-a. (No menu **Arquivo**, selecione **Fechar Solução**.)  
  
## <a name="create-a-new-windows-form"></a>Criar um novo Windows Form  
 Em seguida, você criará um Windows Form.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Para criar o formulário do Windows para este passo a passo  
  
1. No menu **Arquivo**, escolha **Novo** e clique em **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** aparecerá.  
  
2. No painel Tipos de Projeto, abra o nó **Visual Basic**, **Visual C#** ou **Visual C++**, em seguida,  
  
    1. Para Visual Basic ou Visual C#, selecione o nó **Windows** e, em seguida, selecione **aplicativo do Windows Form** no painel **modelos** .  
  
    2. Para Visual C++, selecione o nó **CLR** e, em seguida, selecione **aplicativo do Windows Form** no painel **modelos** .  
  
3. No painel **Modelos**, selecione **Aplicativos do Windows**.  
  
4. Na caixa **Nome**, dê ao projeto um nome exclusivo (por exemplo, Walkthrough_SimpleDebug).  
  
5. Clique em **OK**.  
  
     O Visual Studio cria um novo projeto e exibe um novo formulário no designer do Windows Forms. Para obter mais informações, confira [Designer de Formulários do Windows](https://msdn.microsoft.com/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6. No menu **Exibir**, selecione **Caixa de ferramentas**.  
  
     A caixa de ferramentas é aberta. Para saber mais, confira [Caixa de Ferramentas](../ide/reference/toolbox.md).  
  
7. Na Caixa de ferramentas, clique no controle de **Botão** e arraste-o para a superfície de design do formulário. Remova o botão do formulário.  
  
8. Na caixa de ferramentas, clique no controle **TextBox** e arraste-o para a superfície de design do formulário. Remova **TextBox** do formulário.  
  
9. Na superfície de design do formulário, clique duas vezes no botão.  
  
     Isso leva à página de código. O cursor deve estar em `button1_Click`.  
  
10. Na função `button1_Click`, adicione o seguinte código:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. No menu **Build**, selecione **Compilar Solução**.  
  
     O projeto deve ser compilado sem erros.  
  
## <a name="debug-your-form"></a>Depurar seu formulário  
 Agora, você está pronto para iniciar a depuração.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Para depurar o Windows Form criado para este passo a passo  
  
1. Na janela de origem, clique na margem esquerda na mesma linha que o texto que você adicionou:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Um ponto vermelho aparece e o texto da linha é realçado em vermelho. O ponto vermelho representa um ponto de interrupção. Para obter mais informações, confira [Pontos de interrupção](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Quando você executa o aplicativo no depurador, o depurador interromperá a execução nesse local quando o código é atingido. Você pode exibir o estado do aplicativo e depurá-lo.  
  
    > [!NOTE]
    > Você também pode clicar com o botão direito do mouse em qualquer linha de código, apontar para **Ponto de Interrupção** e clicar em **Inserir Ponto de Interrupção** para adicionar um ponto de interrupção nessa linha.  
  
2. No menu **Depurar**, escolha **Iniciar**.  
  
     O Windows Form começa a ser executado.  
  
3. No Windows Form, clique no botão que você adicionou.  
  
     No Visual Studio, isso o leva à linha onde você definiu seu ponto de interrupção na página de código. Essa linha deve ser realçada em amarelo. Agora você pode exibir as variáveis em seu aplicativo e controlar sua execução. Seu aplicativo parou de executar, aguardando uma ação.  
  
4. No menu **Depurar**, escolha **Windows**, em seguida, **Inspeção** e clique em **Watch1**.  
  
5. Na janela **Watch1**, clique em uma linha em branco. Na coluna **nome** , digite `textBox1.Text` (se você estiver usando Visual Basic, Visual C# ou J#) ou `textBox1->Text` (se estiver usando C++) e pressione Enter.  
  
     A janela **Watch1** mostra o valor dessa variável entre aspas como:  
  
    ```  
    ""  
    ```  
  
6. No menu **Depurar**, escolha **Intervir**.  
  
     O valor de textBox1. Text é alterado na janela **inspeção1** para:  
  
    ```  
    Button was clicked!  
    ```  
  
7. No menu **Depurar**, escolha **Continuar** para retomar a depuração do programa.  
  
8. No Windows Form, clique no botão novamente.  
  
     O Visual Studio interromperá a execução novamente.  
  
9. Clique no ponto vermelho que representa o ponto de interrupção.  
  
     Isso remove o ponto de interrupção do seu código.  
  
10. No menu **Depurar**, escolha **Parar depuração**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Anexar ao seu aplicativo do Windows Form para depurar  
 No [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], você pode anexar o depurador a um processo em execução. Se você estiver usando um Express Edition, esse recurso não terá suporte.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Para anexar ao aplicativo do Windows Form para depurar  
  
1. No projeto que você criou anteriormente, clique na margem esquerda para definir mais uma vez um ponto de interrupção na linha que você adicionou:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2. No menu **Depurar**, selecione **Iniciar Sem Depurar**.  
  
     O Windows Form inicia a execução no Windows, como se você tivesse clicado duas vezes em seu executável. O depurador não está anexado.  
  
3. No menu **depurar** , selecione **anexar ao processo**. (Esse comando também está disponível no menu **ferramentas** .)  
  
     A caixa de diálogo **Anexar ao Processo** é exibida.  
  
4. No painel **processos disponíveis** , localize o nome do processo (Walkthrough_SimpleDebug.exe) na coluna **processo** e clique nele.  
  
5. Clique no botão **anexar** .  
  
6. No seu Windows Form, clique no único botão.  
  
     O depurador interromperá a execução do Windows Form no ponto de interrupção.  
  
## <a name="see-also"></a>Consulte Também  
 [Depuração de código gerenciado](../debugger/debugging-managed-code.md)   
 [Segurança do depurador](../debugger/debugger-security.md)
