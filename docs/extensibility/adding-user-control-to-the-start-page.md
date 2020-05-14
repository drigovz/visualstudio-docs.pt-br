---
title: Adicionando controle de usuário à página inicial | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740135"
---
# <a name="add-user-control-to-the-start-page"></a>Adicione o controle do usuário à página inicial

Este passo a passo mostra como adicionar uma referência DLL a uma página inicial personalizada. O exemplo adiciona um controle do usuário à solução, constrói o controle do usuário e, em seguida, faz referência ao conjunto construído a partir do arquivo Iniciar *.xaml.* Uma nova guia hospeda o controle do usuário, que funciona como um navegador da Web básico.

Você pode usar o mesmo processo para adicionar qualquer conjunto que possa ser chamado de um arquivo *.xaml.*

## <a name="add-a-wpf-user-control-to-the-solution"></a>Adicione um controle de usuário WPF à solução

Primeiro, adicione um controle de usuário do Windows Presentation Foundation (WPF) à solução De página inicial.

1. Crie uma página inicial usando o createino create [a create a custom Start Page](../extensibility/creating-a-custom-start-page.md).

2. No **Solution Explorer,** clique com o botão direito do mouse na solução, clique **em Adicionar**e clique em Novo **Projeto**.

3. No painel esquerdo da caixa de diálogo **Novo Projeto,** expanda o nó **Visual Basic** ou **Visual C#** e clique em **Windows**. No painel do meio, selecione **WPF User Control Library**.

4. Nomeie `WebUserControl` o controle e clique em **OK**.

## <a name="implement-the-user-control"></a>Implementar o controle do usuário

Para implementar um controle de usuário WPF, construa a interface do usuário (UI) em XAML e, em seguida, escreva os eventos de código atrás em C# ou outro idioma .NET.

### <a name="to-write-the-xaml-for-the-user-control"></a>Para escrever o XAML para o controle do usuário

1. Abra o arquivo XAML para o controle do usuário. No `<Grid>` elemento, adicione as seguintes definições de linha ao controle.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. No elemento `<Grid>` principal, adicione `<Grid>` o novo elemento a seguir, que contém uma caixa de texto para digitar endereços da Web e um botão para definir o novo endereço.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Adicione o quadro a seguir `<Grid>` ao elemento `<Grid>` de nível superior logo após o elemento que contém o botão e a caixa de texto.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. O exemplo a seguir mostra o XAML concluído para o controle do usuário.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Para escrever os eventos de código por trás para o controle do usuário

1. No designer XAML, clique duas vezes no botão **Definir endereço** que você adicionou ao controle.

    O arquivo *UserControl1.cs* é aberto no editor de código.

2. Preencha o SetButton_Click Manipulador de Eventos da seguinte forma.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Este código define o endereço da Web digitado na caixa de texto como o destino do navegador da Web. Se o endereço não for válido, o código atira um erro.

3. Você também deve lidar com o evento WebFrame_Navigated:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Compile a solução.

## <a name="add-the-user-control-to-the-start-page"></a>Adicione o controle do usuário à página inicial

Para disponibilizar esse controle ao projeto Iniciar página, no arquivo de projeto Página Inicial, adicione uma referência à nova biblioteca de controle. Em seguida, você pode adicionar o controle à marcação Iniciar página XAML.

1. No **Solution Explorer**, no projeto Iniciar página, clique com o botão direito do mouse **Referências** e clique em **Adicionar referência**.

2. Na guia **Projetos,** selecione **WebUserControl** e clique em **OK**.

3. No menu **Compilar**, clique em **Compilar Solução**.

    A construção da solução torna o controle do usuário disponível para o IntelliSense para outros arquivos na solução.

    Para adicionar o controle à marcação XAML da página inicial, adicione uma referência de namespace ao conjunto e, em seguida, coloque o controle na página.

### <a name="to-add-the-control-to-the-markup"></a>Para adicionar o controle à marcação

1. No **Solution Explorer,** abra o arquivo Iniciar Página *.xaml.*

2. No painel **XAML,** adicione a seguinte declaração de <xref:System.Windows.Controls.Grid> namespace ao elemento de nível superior.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. No painel **XAML,** role \<até a seção Grade>.

    A seção <xref:System.Windows.Controls.TabControl> contém <xref:System.Windows.Controls.Grid> um elemento em um elemento.

4. Adicione \<um elemento TabControl \<> contendo um> TabItem que contém uma referência ao controle do usuário.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Agora você pode testar o controle.

## <a name="test-a-manually-created-custom-start-page"></a>Teste uma página inicial personalizada criada manualmente

1. Copie seu arquivo XAML e quaisquer arquivos de texto ou arquivos de marcação de suporte para a pasta *%USERPROFILE%\Meus Documentos\Visual Studio 2015\StartPages.\\ *

2. Se a página inicial fizer referência a quaisquer controles ou tipos em conjuntos que não estejam instalados pelo Visual Studio, copie os conjuntos e cole-os na _pasta de instalação do Visual Studio_**\Common7\IDE\PrivateAssemblies\\**.

3. Em um prompt de comando do Visual Studio, **digite devenv /rootsufix Exp** para abrir uma instância experimental do Visual Studio.

4. Na instância experimental, vá para a página**Iniciar** o**Ambiente** > **de Opções** >  **de Ferramentas** > e selecione seu arquivo XAML a partir da **lista inicialização** da página inicial.

5. No menu **Exibir,** clique **em Iniciar página**.

    Sua página inicial personalizada deve ser exibida. Se você quiser alterar qualquer arquivo, você deve fechar a instância experimental, fazer as alterações, copiar e colar os arquivos alterados e, em seguida, reabrir a instância experimental para visualizar as alterações.

## <a name="see-also"></a>Confira também

- [Controles de contêiner WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Passo a passo: Adicione XAML personalizado à página inicial](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
