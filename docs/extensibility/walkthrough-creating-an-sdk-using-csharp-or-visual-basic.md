---
title: 'Passo a passo: Criando um SDK usando C# ou Visual Basic | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697554"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Passo a passo: Crie um SDK usando C# ou Visual Basic
Neste passo a passo, você aprenderá a criar um SDK simples da Biblioteca de Matemática usando o Visual C# e, em seguida, empacotar o SDK como uma Extensão visual studio (VSIX). Você completará os seguintes procedimentos:

- [Para criar o componente SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Para criar o projeto de extensão SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Para criar um aplicativo de exemplo que usa a biblioteca de classes](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Pré-requisitos
 Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>Para criar o componente SimpleMath Windows Runtime

1. Na barra de menu, escolha **Arquivo** > **Novo** > **Projeto**.

2. Na lista de modelos, **expanda visual C#** ou **Visual Basic,** escolha o nó **da Windows Store** e escolha o modelo componente de tempo de **execução do Windows.**

3. Na caixa **Nome,** especifique **SimpleMath**e escolha o botão **OK.**

4. No **Solution Explorer,** abra o menu de atalho para o nó do projeto **SimpleMath** e, em seguida, escolha **Propriedades**.

5. Renomeie **Class1.cs** para **Arithmetic.cs** e atualizá-lo para corresponder ao seguinte código:

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. No **Solution Explorer,** abra o menu de atalho para o nó **'SimpleMath' da solução** e, em seguida, escolha O **Gerenciador de configuração**.

    A caixa de diálogo **Gerenciador de configuração** é aberta.

7. Na **lista de configuração da solução Ativa,** escolha **Liberar**.

8. Na coluna **Configuração,** verifique se a linha **SimpleMath** está definida como **'Liberar'** e escolha o botão **Fechar** para aceitar a alteração.

   > [!IMPORTANT]
   > O SDK para o componente SimpleMath inclui apenas uma configuração. Esta configuração deve ser a compilação de versão, ou [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]os aplicativos que usam o componente não passarão pela certificação para o .

9. No **Solution Explorer,** abra o menu de atalho para o nó do projeto **SimpleMath** e, em seguida, escolha **'Construir ''Criar'.**

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>Para criar o projeto de extensão SimpleMathVSIX

1. No menu de atalho para o nó **'SimpleMath' da solução,** escolha **Adicionar** > **novo projeto**.

2. Na lista de modelos, expanda **visual C#** ou **Visual Basic,** escolha o nó **extensibility** e escolha o modelo **do Projeto VSIX.**

3. Na caixa **Nome,** especifique **SimpleMathVSIX**e escolha o botão **OK.**

4. No **Solution Explorer,** escolha o item **source.extension.vsixmanifest.**

5. Na barra de menu, escolha **'Código de exibição '''Exibir'.** > **Code**

6. Substitua o XML existente pelo seguinte XML:

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. No **Solution Explorer,** escolha o projeto **SimpleMathVSIX.**

8. Na barra de menu, escolha **Projeto** > **Adicionar novo item**.

9. Na lista de **Itens Comuns,** expanda **dados**e escolha **Arquivo XML**.

10. Na caixa **Nome,** especifique `SDKManifest.xml`e escolha o botão **Adicionar.**

11. No **Solution Explorer,** abra `SDKManifest.xml`o menu de atalho para , escolha **Propriedades**e altere o valor da propriedade Incluir na propriedade **VSIX** para **True**.

12. Substitua o conteúdo do arquivo pelo XML a seguir:

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. No **Solution Explorer,** abra o menu de atalho para o projeto **SimpleMathVSIX,** escolha **Adicionar**e escolha **Nova pasta**.

14. Renomear a `references`pasta para .

15. Abra o menu de atalho para a pasta **Referências,** escolha **Adicionar**e, em seguida, escolha **Nova pasta**.

16. Renomeie a `commonconfiguration`subpasta para, crie uma subpasta `neutral`dentro dela e nomeie a subpasta .

17. Repita as quatro etapas anteriores, desta `redist`vez renomeando a primeira pasta para .

     O projeto agora contém a seguinte estrutura de pasta:

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. No **Solution Explorer,** abra o menu de atalho para o projeto **SimpleMath** e, em seguida, escolha **Abrir pasta no File Explorer**.

19. No **Explorador de**arquivos, navegue até a pasta *bin\Release,* abra o menu de atalho para o arquivo **SimpleMath.winmd** e, em seguida, escolha **Copiar**.

20. No **Solution Explorer,** cole o arquivo na pasta *references\commonconfiguration\neutral* no projeto **SimpleMathVSIX.**

21. Repita a etapa anterior, colando o arquivo **SimpleMath.pri** na pasta *redist\commonconfiguration\neutral* no projeto **SimpleMathVSIX.**

22. No **Solution Explorer,** escolha **SimpleMath.winmd**.

23. Na barra de menus, escolha**Propriedades de** **exibição** > (Teclado: Escolha a tecla **F4).**

24. Na janela **Propriedades,** altere a propriedade **Build Action** para **Conteúdo**e altere a propriedade Incluir na propriedade **VSIX** para **True**.

25. No **Solution Explorer,** repita este processo para **SimpleMath.pri**.

26. No **Solution Explorer,** escolha o projeto **SimpleMathVSIX.**

27. Na barra de menu, escolha **Build** > **SimpleMathVSIX**.

28. No **Solution Explorer,** abra o menu de atalho para o projeto **SimpleMathVSIX** e, em seguida, escolha **Abrir pasta no File Explorer**.

29. No **File Explorer,** navegue até *\bin\Release* folder e execute *SimpleMathVSIX.vsix* para instalá-la.

30. Escolha o botão **Instalar,** aguarde o término da instalação e, em seguida, reinicie o Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Para criar um aplicativo de exemplo que usa a biblioteca de classes

1. Na barra de menu, escolha **Arquivo** > **Novo** > **Projeto**.

2. Na lista de modelos, **expanda visual C#** ou **Visual Basic**e escolha o nó da **Windows Store.**

3. Escolha o modelo **do aplicativo em branco,** nomeie o projeto **AritméticoUI**e escolha o botão **OK.**

4. No **Solution Explorer,** abra o menu de atalho para o projeto **AritméticoUI** e escolha **Adicionar** > **referência**.

5. Na lista de tipos de referência, expanda o **Windows**e escolha **Extensões**.

6. No painel de detalhes, escolha a extensão da **Biblioteca de Matemática WinRT.**

    Informações adicionais sobre seu SDK são exibidas. Você pode escolher o link https://msdn.microsoft.com/Mais **Informações** para abrir, como você especificou no arquivo SDKManifest.xml anteriormente neste passo a passo.

7. Na caixa de diálogo **Gerenciador de referência,** selecione a caixa de seleção **Da Biblioteca de Matemática WinRT** e escolha o botão **OK.**

8. Na barra de menu, escolha **'Exibir** > **navegador de objetos**' .

9. Na lista **Procurar,** escolha **Matemática Simples**.

     Agora você pode explorar o que está no SDK.

10. No **Solution Explorer,** abra **mainpage.xaml**e substitua seu conteúdo pelo seguinte XAML:

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Atualização **MainPage.xaml.cs** para corresponder ao seguinte código:

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Escolha a chave **F5** para executar o aplicativo.

13. No aplicativo, digite dois números, escolha uma **=** operação e escolha o botão.

     O resultado correto aparece.

    Você criou e usou com sucesso um SDK de extensão.

## <a name="see-also"></a>Confira também
- [Passo a passo: Crie um SDK usando C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Passo a passo: crie um SDK usando JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Criar um Software Development Kit](../extensibility/creating-a-software-development-kit.md)
