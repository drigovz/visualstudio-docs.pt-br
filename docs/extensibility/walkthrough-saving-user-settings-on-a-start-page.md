---
title: 'Passo a passo: Salvando configurações do usuário em uma página inicial | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697087"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Passo a passo: Salve as configurações do usuário em uma página inicial

Você pode persistir as configurações do usuário para sua Página Inicial. Ao seguir este passo a passo, você pode criar um controle que salva uma configuração no registro quando o usuário clica em um botão e, em seguida, recupera essa configuração toda vez que a Página inicial é carregada. Como o modelo de projeto Iniciar página inclui um controle de usuário personalizável e as chamadas XAML da página inicial padrão, você não precisa modificar a própria Página Inicial.

A loja de configurações que é instanciada neste <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> passo a passo é uma instância da interface, que lê e grava para o seguinte local de registro quando é chamada: **HKCU\Software\Microsoft\VisualStudio\14.0\\\<CollectionName>**

Quando ele está sendo executado na instância experimental do Visual Studio, a loja de configurações lê e grava para **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<CollectionName>.**

Para obter mais informações sobre como persistir as configurações, consulte [Estendendo as configurações e opções do usuário](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Pré-requisitos

> [!NOTE]
> Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> Você pode baixar o modelo de projeto Iniciar página usando **o Extension Manager**.

## <a name="set-up-the-project"></a>Configurar o projeto

1. Crie um projeto de página inicial conforme descrito em [Criar uma página inicial personalizada](creating-a-custom-start-page.md). Nomeie o projeto **SaveMySettings**.

2. No **Solution Explorer,** adicione as seguintes referências de montagem ao projeto StartPageControl:

    - Envdte

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Abra *MyControl.xaml*.

4. A partir do painel XAML, <xref:System.Windows.Controls.UserControl> na definição de elemento de nível superior, adicione a seguinte declaração de evento após as declarações de namespace.

    ```xml
    Loaded="OnLoaded"
    ```

5. No painel de design, clique na área principal do controle e, em seguida, **pressione Excluir**.

     Esta etapa remove <xref:System.Windows.Controls.Border> o elemento e tudo nele, <xref:System.Windows.Controls.Grid> e deixa apenas o elemento de nível superior.

6. A partir da caixa <xref:System.Windows.Controls.StackPanel> de **ferramentas,** arraste um controle para a grade.

7. Agora arraste <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox>um botão e <xref:System.Windows.Controls.StackPanel>um botão para o .

8. Adicione um atributo **x:Nome** para o <xref:System.Windows.Controls.TextBox>, e um `Click` evento para o <xref:System.Windows.Controls.Button>, como mostrado no exemplo a seguir.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementar o controle do usuário

1. No painel XAML, clique com `Click` o <xref:System.Windows.Controls.Button> botão direito do mouse no atributo do elemento e clique **em Navegar para O Manipulador de Eventos**.

     Esta etapa abre *MyControl.xaml.cs*e cria `Button_Click` um manipulador de stubs para o evento.

2. Adicione as `using` seguintes diretivas à parte superior do arquivo.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Adicione uma `SettingsStore` propriedade privada, como mostrado no exemplo a seguir.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Esta propriedade primeiro recebe <xref:EnvDTE80.DTE2> uma referência à interface, que <xref:System.Windows.FrameworkElement.DataContext%2A> contém o modelo de objeto Automação, a partir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> do controle do usuário, e depois usa o DTE para obter uma instância da interface. Em seguida, ele usa essa instância para retornar as configurações atuais do usuário.

4. Preencha o `Button_Click` evento da seguinte forma.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     Isso grava o conteúdo da caixa de texto para um campo "MySetting" em uma coleção "MySettings" no registro. Se a coleção não existe, ela é criada.

5. Adicione o seguinte `OnLoaded` manipulador para o evento do controle do usuário.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Este código define o texto da caixa de texto para o valor atual de "MySetting".

6. Construa o controle do usuário.

7. Em **Solution Explorer,** open *source.extension.vsixmanifest*.

8. No editor manifesto, defina o **nome do produto** para salvar a página inicial de **configurações**.

     Este recurso define o nome da Página Inicial como deve aparecer na lista **Personalizar página inicial** na caixa de diálogo **Opções.**

9. Construa *StartPage.xaml*.

## <a name="test-the-control"></a>Testar o controle

1. Pressione **F5**.

     A instância experimental do Visual Studio abre.

2. Na instância experimental, no menu **Ferramentas,** clique em **Opções**.

3. No nó **Ambiente,** clique em **Iniciar**e, em seguida, na lista **Personalizar a página inicial,** selecione **[Extensão instalada] Salve minha página inicial de configurações**.

     Clique em **OK**.

4. Feche a página inicial se estiver aberta e, em seguida, no menu **Exibir,** clique em **Iniciar página**.

5. Na página inicial, clique na guia **MyControl.**

6. Na caixa de texto, **digite Cat**e clique **em Salvar minha configuração**.

7. Feche a página inicial e abra novamente.

     A palavra "Gato" deve ser exibida na caixa de texto.

8. Substitua a palavra "Gato" pela palavra "Cão". Não clique no botão.

9. Feche a página inicial e abra novamente.

     A palavra "Cão" deve ser exibida na caixa de texto, mesmo que você não tenha salvado a configuração porque o Visual Studio mantém janelas de ferramentas na memória, mesmo que estejam fechadas, até que o próprio Visual Studio feche.

10. Feche a instância experimental do Visual Studio.

11. Pressione **F5** para reabrir a instância experimental.

12. A palavra "Gato" deve ser exibida na caixa de texto.

## <a name="next-steps"></a>Próximas etapas

Você pode modificar este controle do usuário para salvar e recuperar qualquer número de configurações `SettingsStore` personalizadas usando valores diferentes de diferentes manipuladores de eventos para obter e definir a propriedade. Desde que você use `propertyName` um parâmetro diferente <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>para cada chamada, os valores não sobreescrevem um ao outro no registro.

## <a name="see-also"></a>Confira também

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Adicionando comandos do Visual Studio a uma página inicial](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
