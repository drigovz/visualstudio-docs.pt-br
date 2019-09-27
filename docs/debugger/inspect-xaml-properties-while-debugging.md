---
title: Inspecionar propriedades XAML durante a depuração | Microsoft Docs
ms.date: 03/06/2017
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 182c9e37764a247ec24b4b477975ccb7b8811c4b
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322542"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Inspecione as propriedades XAML durante a depuração
Você pode obter uma visão em tempo real de seu código XAML em execução com a **árvore visual ao** vivo e o **Gerenciador de propriedades ao vivo**. Essas ferramentas fornecem uma exibição de árvore dos elementos de interface do usuário do seu aplicativo XAML em execução e mostram as propriedades de tempo de execução de qualquer elemento de interface do usuário que você selecionar.

Você pode usar essas ferramentas nas seguintes configurações:

|Tipo de aplicativo|Sistema operacional e ferramentas|
|-----------------|--------------------------------|
|Aplicativos Windows Presentation Foundation (4,0 e superior)|Windows 7 e posterior|
|Aplicativos Universais do Windows|Windows 10 e posterior, com o [SDK do Windows 10](https://dev.windows.com/en-us/downloads/windows-10-sdk)|

## <a name="looking-at-elements-in-the-live-visual-tree"></a>Examinando elementos na árvore visual ativa
Vamos começar com um aplicativo WPF muito simples que tem um modo de exibição de lista e um botão. Cada vez que você clica no botão, outro item é adicionado à lista. Os itens de números pares são coloridos em cinza e os itens ímpares são coloridos em amarelo.

Crie um novo C# aplicativo do WPF (arquivo > novo projeto de >, C# em seguida, selecione e localize aplicativo do WPF). Nomeie-o como **TestXAML**.

Altere MainWindow. XAML para o seguinte:

```xaml
<Window x:Class="TestXAML.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:local="clr-namespace:TestXAML"
    mc:Ignorable="d"
    Title="MainWindow" Height="350" Width="525">
    <Grid>
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>
    </Grid>
</Window>
```

Adicione o seguinte manipulador de comando ao arquivo MainWindow.xaml.cs:

```csharp
int count;

private void button_Click(object sender, RoutedEventArgs e)
{
    ListBoxItem item = new ListBoxItem();
    item.Content = "Item" + ++count;
    if (count % 2 == 0)
    {
        item.Background = Brushes.LightGray;
    }
    else
    {
        item.Background = Brushes.LightYellow;
    }
    listBox.Items.Add(item);
}
```

Compile o projeto e comece a depuração. (A configuração de compilação deve ser Debug, não Release. Para saber mais sobre configurações de build, confira [Noções básicas sobre configurações de build](../ide/understanding-build-configurations.md).

Quando a janela aparecer, clique no botão **Adicionar item** algumas vezes. Você deve ver algo parecido com isso:

![Janela principal do aplicativo](../debugger/media/livevisualtree-app.png "LiveVIsualTree-aplicativo")

Agora, abra a janela de **árvore visual ao vivo** (**depuração > árvore visual do Windows > Live**ou encontre-a no lado esquerdo do IDE). Arraste-o para fora da posição de encaixe para que possamos examinar essa janela e a janela de **propriedades dinâmicas** lado a lado. Na janela da **árvore visual ao vivo** , expanda o nó **ContentPresenter** . Ele deve conter nós para o botão e a caixa de listagem. Expanda a caixa de listagem (e, em seguida, **ScrollContentPresenter** e **ItemsPresenter**) para localizar os itens da caixa de listagem. A janela deve ter a seguinte aparência:

![ListBoxItems na árvore visual ao vivo](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")

Volte para a janela do aplicativo e adicione mais alguns itens. Você deverá ver mais itens da caixa de listagem aparecerem na **árvore visual ao vivo**.

Agora, vamos examinar as propriedades de um dos itens da caixa de listagem. Selecione o primeiro item da caixa de listagem na **árvore visual ao vivo** e clique no ícone **mostrar propriedades** na barra de ferramentas. O **Gerenciador de propriedades ao vivo** deve aparecer. Observe que o campo de **conteúdo** é "Item1" e o campo de**cor** do **plano de fundo** > é **#FFFFFFE0**. Volte para a **árvore visual ao vivo** e selecione o segundo item da caixa de listagem. O **Gerenciador de propriedades ao vivo** deve mostrar que o campo de **conteúdo** é "Item2" e o campo de**cor** de **plano de fundo** > é **#FFD3D3D3**.

> [!NOTE]
> Uma borda amarela em torno de uma propriedade no **Gerenciador de propriedades ao vivo** significa que o valor da propriedade é definido por meio `Color = {BindingExpression}`de uma associação, como. Uma borda verde significa que o valor é definido usando um recurso, como `Color = {StaticResource MyBrush}`.

A estrutura real do XAML tem muitos elementos dos quais você provavelmente não está interessado diretamente e, se você não souber o código, poderá ter um tempo rígido para navegar pela árvore e encontrar o que está procurando. Portanto, a **árvore visual ativa** tem algumas maneiras que permitem usar a interface do usuário do aplicativo para ajudá-lo a encontrar o elemento que deseja examinar.

**Habilitar seleção no aplicativo em execução**. Você pode habilitar esse modo quando seleciona o botão mais à esquerda na barra de ferramentas da **árvore visual ativa** . Com esse modo ativado, você pode selecionar um elemento de interface do usuário no aplicativo e a **árvore visual dinâmica** (e o **Visualizador de propriedades ao vivo**) é atualizada automaticamente para mostrar o nó na árvore correspondente a esse elemento e suas propriedades.

**Exibir adornos de layout no aplicativo em execução**. Você pode habilitar esse modo ao selecionar o botão que está imediatamente à direita do botão habilitar seleção. Quando o **layout de exibição adorners** está ativado, faz com que a janela do aplicativo mostre linhas horizontais e verticais ao longo dos limites do objeto selecionado para que você possa ver o que ele alinha, bem como os retângulos que mostram as margens. Por exemplo, ative **habilitar seleção** e **Exibir layout** em e selecione o bloco de texto **Adicionar item** no aplicativo. Você deve ver o nó bloco de texto na **árvore visual ao vivo** e as propriedades de bloco de texto no **Visualizador de propriedades ao vivo**, bem como as linhas horizontais e verticais nos limites do bloco de texto.

![LivePropertyViewer em DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

**Visualizar Seleção**. Você pode habilitar esse modo selecionando o terceiro botão à esquerda na barra de ferramentas da árvore visual ao vivo. Esse modo mostra o XAML em que o elemento foi declarado, se você tiver acesso ao código-fonte do aplicativo. Selecione **habilitar seleção** e **Visualizar seleção**e, em seguida, selecione o botão em nosso aplicativo de teste. O arquivo MainWindow. XAML é aberto no Visual Studio e o cursor é colocado na linha em que o botão é definido.

## <a name="using-xaml-tools-with-running-applications"></a>Usando ferramentas XAML com aplicativos em execução
Você pode usar essas ferramentas XAML mesmo quando não tiver o código-fonte. Ao anexar a um aplicativo XAML em execução, você também pode usar a **árvore visual ao vivo** nos elementos da interface do usuário desse aplicativo. Veja um exemplo, usando o mesmo aplicativo de teste do WPF que usamos antes.

1. Inicie o aplicativo **TestXaml** na configuração de versão. Não é possível anexar a um processo que está sendo executado em uma configuração de **depuração** .

2. Abra uma segunda instância do Visual Studio e clique em **depurar > anexar ao processo**. Localize **TestXaml. exe** na lista de processos disponíveis e clique em **anexar**.

3. O aplicativo começa a ser executado.

4. Na segunda instância do Visual Studio, abra a **árvore visual ao vivo** (**depuração > árvore visual do Windows > Live**). Você deve ver os elementos da interface do usuário do **TestXaml** , e você deve ser capaz de manipulá-los como fez ao depurar o aplicativo diretamente.

## <a name="see-also"></a>Consulte também

[Gravar e depurar o código XAML em execução com o Hot recarregamento de XAML](xaml-hot-reload.md)
