---
title: 'Tutorial: aplicativo Olá, Mundo com o Windows Presentation Foundation (WPF) em C#'
description: Crie um aplicativo .NET de Área de Trabalho do Windows simples em C# com o Visual Studio usando a estrutura de interface do usuário do Windows Presentation Foundation (WPF).
ms.custom: seodec18, get-started
ms.date: 03/14/2019
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 173f2320b0117d31cbd3d0b999f2e24c40a5860b
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58325178"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Tutorial: Criar um aplicativo simples com o C\#

Ao concluir este tutorial, você estará familiarizado com vários designers, ferramentas e caixas de diálogo que poderão ser usados no desenvolvimento de aplicativos com o Visual Studio. Você vai criar um aplicativo "Olá, Mundo", projetar a interface do usuário, adicionar código e depurar erros enquanto aprende sobre o trabalho no [IDE](visual-studio-ide.md) (ambiente de desenvolvimento integrado).

::: moniker range="vs-2017"
Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) para instalá-lo gratuitamente.
::: moniker-end
::: moniker range=">=vs-2019"
Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) para instalá-lo gratuitamente.
::: moniker-end

## <a name="configure-the-ide"></a>Configurar o IDE

::: moniker range="vs-2017"

Ao abrir o Visual Studio pela primeira vez, você será solicitado a entrar. Esta etapa é opcional neste tutorial. Em seguida, você poderá ver uma caixa de diálogo que solicita a escolha das configurações de desenvolvimento e o tema de cores. Mantenha os padrões e escolha **Iniciar o Visual Studio**.

![Caixa de diálogo Escolher configurações](../media/exploreide-settings.png)

Depois que o Visual Studio for iniciado, você verá as janelas de ferramentas, os menus e as barras de ferramentas, bem como o espaço da Janela principal. As janelas de ferramentas estão encaixadas nos lados esquerdo e direito da janela do aplicativo, com **Início Rápido**, a barra de menus e a barra de ferramentas padrão na parte superior. No centro da janela do aplicativo está a **Página Inicial**. Ao carregar uma solução ou um projeto, os editores e designers são exibidos no espaço em que a **Página Inicial** está localizada. Ao desenvolver um aplicativo, você passará a maior parte do seu tempo nessa área central.

![IDE do Visual Studio 2017 com as configurações gerais aplicadas](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Quando você inicia o Visual Studio, a janela de início é aberta primeiro. Selecione **Continuar sem código** para abrir o ambiente de desenvolvimento. Você verá as janelas de ferramentas, os menus e as barras de ferramentas, além do espaço da janela principal. As janelas de ferramentas estão encaixadas nos lados esquerdo e direito da janela do aplicativo, com **Início Rápido**, a barra de menus e a barra de ferramentas padrão na parte superior. Quando você carrega uma solução ou um projeto, os editores e designers são exibidos no espaço central da janela do aplicativo. Ao desenvolver um aplicativo, você passará a maior parte do seu tempo nessa área central.

::: moniker-end

## <a name="create-the-project"></a>Criar o projeto

Ao criar um aplicativo no Visual Studio, você cria primeiro um projeto e uma solução. Para este exemplo, você criará um projeto do WPF (Windows Presentation Foundation).

1. Crie um novo projeto. Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto**.

     ::: moniker range="vs-2017"
     ![Na barra de menus, escolha Arquivo, Novo, Projeto](../media/exploreide-filenewproject.png)
     ::: moniker-end
     ::: moniker range=">=vs-2019"
     [Na barra de menus, escolha Arquivo, Novo, Projeto](../media/vs-2019/exploreide-filenewproject-vs2019.png)
     ::: moniker-end

::: moniker range="vs-2017"
2. Na caixa de diálogo **Novo Projeto**, selecione a categoria **Instalado** > **Visual C#** > **Área de Trabalho do Windows** e, em seguida, selecione o modelo **Aplicativo WPF (.NET Framework)**. Nomeie o projeto como **HelloWPFApp** e selecione **OK**.

     ![Modelo do aplicativo WPF na caixa de diálogo Novo Projeto do Visual Studio](media/exploreide-newprojectcsharp.png)
::: moniker-end
::: moniker range=">=vs-2019"
2. Na tela **Criar um novo projeto**, pesquise por "WPF" e escolha **Aplicativo WPF (.NET Framework)** e, em seguida, escolha **Avançar**.

   ![Modelo do aplicativo WPF na caixa de diálogo Novo Projeto do Visual Studio](media/vs-2019/exploreide-newprojectcsharp-vs2019.png)

3. Na próxima tela, dê o nome **HelloWPFApp** ao projeto e escolha **Criar**.
::: moniker-end

O Visual Studio cria o projeto e a solução HelloWPFApp e o **Gerenciador de Soluções** mostra os diversos arquivos. O **Designer do WPF** mostra um modo de exibição de Design e um modo de exibição XAML de *MainWindow.xaml* em um modo divisão. É possível deslizar o divisor para mostrar mais ou menos de cada exibição. É possível optar por ver apenas a exibição visual ou apenas a exibição XAML. Os seguintes itens aparecem no **Gerenciador de Soluções**:

::: moniker range="vs-2017"
![Gerenciador de Soluções com arquivos HelloWPFApp carregados](../media/exploreide-hellowpfappfiles.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Gerenciador de Soluções com arquivos HelloWPFApp carregados](../media/vs-2019/exploreide-hellowpfappfiles.png)
::: moniker-end

> [!NOTE]
> Para saber mais informações sobre XAML (eXtensible Application Markup Language), confira a página [Visão geral do XAML para WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Depois de criar o projeto, você poderá personalizá-lo. Ao usar a janela **Propriedades** (encontrada no menu **Exibir**), é possível exibir e alterar opções para itens de projeto, controles e outros itens em um aplicativo.

### <a name="change-the-name-of-mainwindowxaml"></a>Alterar o nome de MainWindow.xaml

Vamos dar um nome mais específico para MainWindow.

1. No **Gerenciador de Soluções**, selecione *MainWindow.xaml*. Você deverá ver a janela **Propriedades**, mas se ela não for exibida, escolha o menu **Exibir** e, em seguida, o item **Janela Propriedades**.

1. Altere a propriedade **Nome de Arquivo** para `Greetings.xaml`.

     ![Janela Propriedades com o nome do arquivo realçado](../media/exploreide-filenameinpropertieswindow.png)

     O **Gerenciador de Soluções** mostra que o nome do arquivo agora é *Greetings.xaml* e o arquivo de código aninhado agora é chamado de *Greetings.xaml.cs*. Esse arquivo de código é aninhado sob o nó do arquivo *.xaml* para mostrar que eles estão intimamente relacionados.

## <a name="design-the-user-interface-ui"></a>Criar a interface do usuário

Adicionaremos três tipos de controles a este aplicativo: um controle <xref:System.Windows.Controls.TextBlock>, dois controles <xref:System.Windows.Controls.RadioButton> e um controle <xref:System.Windows.Controls.Button>.

### <a name="add-a-textblock-control"></a>Adicionar um controle TextBlock

1. Insira **Ctrl**+**Q** para invocar o **Início Rápido** e digite **Caixa de ferramentas**. Escolha **Exibir > Caixa de ferramentas** na lista de resultados.

2. No **Caixa de Ferramentas**, expanda o nó **Controles Comuns do WPF** para ver o controle TextBlock.

     ![Caixa de ferramentas com o controle TextBlock realçado](../media/exploreide-textblocktoolbox.png)

3. Adicione um controle TextBlock à superfície de design escolhendo o item **TextBlock** e arrastando-o para a janela na superfície de design. Centralize o controle próximo à parte superior da janela.

Sua janela deve se parecer com a ilustração a seguir:

![Controle TextBlock no formulário Saudações](../media/exploreide-greetingswithtextblockonly.png)

A marcação XAML deve ter uma aparência semelhante ao exemplo a seguir:

```xaml
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Personalizar o texto no bloco de texto

1. Na exibição XAML, localize a marcação de TextBlock e altere o atributo Text:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. Se necessário, centralize novamente o TextBlock e salve as alterações pressionando Ctrl+S ou usando o item de menu **Arquivo**.

Em seguida, você adicionará dois controles [RadioButton](/dotnet/framework/wpf/controls/radiobutton) ao formulário.

### <a name="add-radio-buttons"></a>Adicionar botões de opção

1. Na **Caixa de Ferramentas**, localize o controle **RadioButton**.

     ![Janela de ferramentas com o controle RadioButton selecionado](../media/exploreide-radiobuttontoolbox.png)

2. Adicione dois controles RadioButton à superfície de design escolhendo o item **RadioButton** e arrastando-o para a janela na superfície de design. Mova os botões (selecionando-os e usando as teclas de direção) para que os botões sejam exibidos lado a lado sob o controle TextBlock.

     A sua janela deve se parecer com esta:

     ![Formulário de saudações com TextBlock e dois botões de opção](../media/exploreide-greetingswithradiobuttons.png)

3. Na janela **Propriedades** do controle RadioButton esquerdo, altere a propriedade **Nome** (a propriedade na parte superior da janela **Propriedades**) para `HelloButton`.

     ![Janela Propriedades RadioButton](../media/exploreide-buttonproperties.png)

4. Na janela **Propriedades** do controle RadioButton direito, altere a propriedade **Name** para `GoodbyeButton` e, em seguida, salve as alterações.

Agora você pode adicionar o texto de exibição para cada controle RadioButton. O procedimento a seguir atualiza a propriedade **Conteúdo** de um controle RadioButton.

### <a name="add-display-text-for-each-radio-button"></a>Adicionar o texto de exibição de cada botão de opção

1. Na área de design, abra o menu de atalho de HelloButton pressionando o botão direito do mouse em HelloButton, escolha **Editar Texto** e, em seguida, insira `Hello`.

2. Abra o menu de atalho de GoodbyeButton pressionando o botão direito do mouse em GoodbyeButton, escolha **Editar Texto** e, em seguida, insira `Goodbye`.

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Definir que um botão de opção faça check-in por padrão

Nesta etapa, definiremos que o HelloButton permaneça marcado por padrão, de maneira que um dos dois botões de opção esteja sempre selecionado.

Na exibição XAML, localize a marcação do HelloButton e adicione um atributo **IsChecked**:

```xaml
IsChecked="True"
```

O elemento final da interface do usuário que você adicionará é um controle de [Botão](/dotnet/framework/wpf/controls/button).

### <a name="add-the-button-control"></a>Adicionar o controle de botão

1. Na **Caixa de Ferramentas**, localize o controle de **Botão** e, em seguida, adicione-o à superfície de design sob os controles RadioButton, arrastando-o para o formulário no modo de exibição de Design.

2. Na exibição XAML, altere o valor de **Conteúdo** do controle de Botão, de `Content="Button"` para `Content="Display"` e salve as alterações.

     A marcação deverá ser semelhante ao exemplo a seguir: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Sua janela deve se parecer com a ilustração a seguir.

     ![Formulário de saudações com rótulos de controle](media/exploreide-greetingswithcontrollabels-cs.png)

### <a name="add-code-to-the-display-button"></a>Adicionar um código ao botão de exibição

Quando esse aplicativo é executado, uma caixa de mensagem é exibida depois que um usuário escolhe um botão de opção e, em seguida, escolhe o botão **Exibir**. Uma caixa de mensagem será exibida para Olá e outra para Até logo. Para criar esse comportamento, adicione um código ao evento `Button_Click` em *Greetings.xaml.cs*.

1. Na superfície de design, clique duas vezes no botão **Exibição**.

     *Greetings.xaml.cs* é aberto, com o cursor no evento `Button_Click`.

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

2. Insira o seguinte código:

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

3. Salve o aplicativo.

## <a name="debug-and-test-the-application"></a>Depurar e testar o aplicativo

Em seguida, você depurará o aplicativo para procurar erros e testar se ambas as caixas de mensagem são exibidas corretamente. As instruções a seguir descrevem como criar e iniciar o depurador, mas, posteriormente, leia [Compilar um aplicativo WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) e [Depurar o WPF](../../debugger/debugging-wpf.md) para obter mais informações.

### <a name="find-and-fix-errors"></a>Localizar e corrigir erros

Nesta etapa, você encontrará o erro que causamos anteriormente alterando o nome do arquivo *MainWindow.xaml*.

#### <a name="start-debugging-and-find-the-error"></a>Iniciar a depuração e localizar o erro

1. Inicie o depurador pressionando **F5** ou selecionando **Depurar** e depois **Iniciar Depuração**.

   Uma janela **Modo de Interrupção** é exibida e a janela de **Saída** indica que ocorreu uma IOException: Não é possível localizar o recurso 'mainwindow.xaml'.

   ![Captura de tela da mensagem de IOException](../media/exploreide-ioexception.png)

2. Interrompa o depurador escolhendo **Depurador** > **Interromper a Depuração**.

Renomeamos o *MainWindow.xaml* como *Greetings.xaml* no início deste tutorial, mas o código ainda se refere a *MainWindow.xaml* como o URI de inicialização do aplicativo. Portanto, o projeto não pode ser iniciado.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Especificar Greetings.xaml como o URI de inicialização

1. No **Gerenciador de Soluções**, abra o arquivo *App.xaml*.

2. Altere `StartupUri="MainWindow.xaml"` para `StartupUri="Greetings.xaml"` e salve as alterações.

Inicie o depurador novamente (pressione **F5**). Você deverá ver a janela **Saudações** do aplicativo. Agora, feche a janela do aplicativo para parar a depuração.

### <a name="debug-with-breakpoints"></a>Depurar com pontos de interrupção

Você pode testar o código durante a depuração ao adicionar alguns pontos de interrupção. Você pode adicionar pontos de interrupção escolhendo **Depurar** > **Ativar/Desativar Ponto de Interrupção**, clicando na margem esquerda do editor ao lado da linha de código em que você deseja que a interrupção ocorra ou pressionando **F9**.

#### <a name="add-breakpoints"></a>Adicionar pontos de interrupção

1. Abra *Greetings.xaml.cs* e selecione a seguinte linha: `MessageBox.Show("Hello.")`

2. Adicione um ponto de interrupção por meio do menu selecionando **Depurar** e, em seguida, **Ativar/Desativar Ponto de Interrupção**.

     Um círculo vermelho aparece ao lado da linha de código na margem da extrema esquerda da janela do editor.

3. Selecione a linha a seguir: `MessageBox.Show("Goodbye.")`.

4. Pressione a tecla **F9** para adicionar um ponto de interrupção e, em seguida, pressione **F5** para iniciar a depuração.

5. Na janela **Saudações**, escolha o botão de opção **Olá** e depois o botão **Exibição**.

    A linha `MessageBox.Show("Hello.")` é realçada em amarelo. Na parte inferior do IDE, as janelas Automáticos, Locais e Inspeção estão encaixadas juntas no lado esquerdo e as janelas Pilha de Chamadas, Pontos de Interrupção, Configurações de Exceção, Comando, Imediato e Saída estão encaixadas no lado direito.

    ![Captura de tela de ponto de interrupção no depurador](media/exploreide-debugbreakpoint.png)

6. Na barra de menus, escolha **Depurar** > **Depuração Circular**.

     O aplicativo retomará a execução e uma caixa de mensagem com a palavra "Olá" será exibida.

7. Escolha o botão **OK** na caixa de mensagem para fechá-la.

8. Na janela **Saudações**, escolha o botão de opção **Até logo** e depois o botão **Exibição**.

     A linha `MessageBox.Show("Goodbye.")` é realçada em amarelo.

9. Escolha a tecla **F5** para continuar a depuração. Quando a caixa de mensagem for exibida, escolha o botão **OK** na caixa de mensagem para fechá-la.

10. Feche a janela do aplicativo para parar a depuração.

11. Na barra de menus, escolha **Depurar** > **Desabilitar Todos os Pontos de Interrupção**.

### <a name="build-a-release-version-of-the-application"></a>Criar uma versão de lançamento do aplicativo

Agora que você verificou que tudo está funcionando, já pode preparar um build de versão do aplicativo.

1. No menu principal, selecione **Build** > **Limpar solução** para excluir arquivos intermediários e arquivos de saída criados durante builds anteriores. Isso não é necessário, mas limpa as saídas de build de depuração.

2. Altere a configuração de build de HelloWPFApp, de **Depuração** para **Versão**, usando o controle suspenso na barra de ferramentas (no momento, seu nome é “Depuração”).

3. Compile a solução escolhendo **Compilar** > **Compilar solução**.

Parabéns por concluir este tutorial. Encontre o *.exe* compilado na solução e no diretório do projeto (*...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="see-also"></a>Consulte também

- [Dicas de produtividade](../../ide/productivity-tips-for-visual-studio.md)