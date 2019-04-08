---
title: 'Passo a passo: Depuração de um formulário da Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee796418658ec0825a76d60607b77813f84e4144
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926274"
---
# <a name="walkthrough-debugging-a-web-form"></a>Passo a passo: Depurando um Formulário da Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As etapas deste passo a passo mostram como depurar um aplicativo Web do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], também conhecido como um Web Form. Mostra como iniciar e interromper a execução, definir pontos de interrupção e examinar variáveis na janela **Inspeção**.  
  
> [!NOTE]
>  Para concluir este passo a passo, você deverá ter privilégios de administrador no computador do servidor. Por padrão, o processo do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], aspnet_wp.exe ou w3wp.exe, é executado como um processo do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Para depurar o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], você deverá ter privilégios de Administrador no computador no qual o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] é executado. Para obter mais informações, consulte [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
 As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-web-form"></a>Para criar o Web Form  
  
1.  Se você já tiver uma solução aberta, feche-a.  
  
2.  No menu **Arquivo**, clique em **Novo** e, em seguida, clique em **Site**.  
  
     A caixa de diálogo **Novo Site** aparece.  
  
3.  No painel **Modelos**, clique no **Site ASP.NET**.  
  
4.  Sobre o **local** linha, clique em **HTTP** na lista e, na caixa de texto, digite **http://localhost/WebSite**.  
  
5.  Na lista **Linguagem**, clique em **Visual C#** ou **Visual Basic**.  
  
6.  Clique em **OK**.  
  
     O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cria um novo projeto e exibe o código-fonte HTML padrão. Ele também cria um novo diretório virtual chamado **WebSite** em **Site Padrão** no IIS.  
  
7.  Clique na guia **Design** na margem inferior.  
  
8.  Clique na guia **Caixa de Ferramentas** na margem esquerda ou selecione-a no menu **Exibir**.  
  
     A **Caixa de ferramentas** é aberta.  
  
9. Na **Caixa de Ferramentas**, clique no controle de **Botão** e adicione-o à superfície de design principal, Default.aspx.  
  
10. Na **Caixa de Ferramentas**, clique no controle **Caixa de Texto** e arraste o controle para a superfície de design principal, Default.aspx.  
  
11. Clique duas vezes no controle de botão que você removeu.  
  
     Isso leva você à página de código: Default.aspx.cs para C# ou default para [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. O cursor deve estar na função `Button1_Click`.  
  
12. Na função `Button1_Click`, adicione o seguinte código:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. No menu **Compilar**, clique em **Compilar Solução**.  
  
     O projeto deve ser compilado sem erros.  
  
     Agora, você está pronto para iniciar a depuração.  
  
### <a name="to-debug-the-web-form"></a>Para depurar o Web Form  
  
1.  Na janelafault.aspx.cs ou Default.aspx.vb, clique na margem esquerda na mesma linha que o texto que você adicionou:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Um ponto vermelho aparece e o texto da linha é realçado em vermelho. O ponto vermelho representa um ponto de interrupção. Quando você executa o aplicativo no depurador, o depurador interromperá a execução nesse local quando o código é atingido. Você pode exibir o estado do aplicativo e depurá-lo. Para obter mais informações, confira [Pontos de interrupção](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  No menu **Depuração**, clique em **Iniciar Depuração**.  
  
3.  A caixa de diálogo **Depuração Não Habilitada** é exibida. Selecione a opção **Modificar o arquivo Web.config para habilitar depuração** e clique em **OK**.  
  
     O Internet Explorer inicia e exibe a página recém-criada.  
  
4.  No Internet Explorer, clique no botão.  
  
     No [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], essa opção leva você à linha onde você define o ponto de interrupção na página de código Default.aspx.cs ou Default.aspx.vb. Essa linha deve ser realçada em amarelo. Agora você pode exibir as variáveis em seu aplicativo e controlar sua execução. Seu aplicativo para a execução e aguarda você enviar um comando.  
  
5.  No menu **Depurar**, clique em **Janelas** e, em seguida, clique em **Inspeção** e em **Watch1**.  
  
6.  Na janela **Inspeção**, digite **TextBox1.Text**.  
  
     A janela **Inspeção** mostra o valor da variável `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7.  No menu **Depurar**, clique em **Percorrer**.  
  
     O valor de `TextBox1.Text` é alterado na janela **Inspeção** para ler:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  No menu **Depurar**, clique em **Continuar**.  
  
9. No Internet Explorer, clique no botão novamente.  
  
     A execução para no ponto de interrupção novamente.  
  
10. Na janelafault.aspx.cs ou Default.aspx.vb, clique no ponto vermelho na margem esquerda:  
  
     Isso remove o ponto de interrupção.  
  
11. No menu **Depurar**, clique em **Parar Depuração**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Para anexar ao Web Form para depurar  
  
1.  No [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], você pode anexar o depurador a um processo em execução. Para obter uma depuração mais efetiva, compile o executável como arquivos da versão de depuração com símbolo (PDB).  
  
2.  Na janelafault.aspx.cs ou Default.aspx.vb, clique na margem esquerda para novamente definir um ponto de interrupção na linha adicionada:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  No menu **Depuração**, clique em **Iniciar sem Depurar**.  
  
     O Web Form começa a ser executado no Internet Explorer, mas o depurador não está anexado.  
  
4.  Anexe ao processo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Para obter mais informações, consulte [Depurando aplicativos de Web implantado](../debugger/debugging-deployed-web-applications.md).  
  
5.  No Internet Explorer, clique no botão no seu formulário.  
  
     No [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], você deve atingir o ponto de interrupção em Default.aspx.cs, Default.aspx.vb ou Default.aspx.  
  
6.  Quando você terminar de depurar, no menu **Depurar**, clique em **Parar Depuração**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)
