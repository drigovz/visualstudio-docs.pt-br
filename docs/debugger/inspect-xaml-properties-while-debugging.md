---
title: Inspecione as propriedades XAML durante a depuração | Microsoft Docs
ms.date: 03/06/2017
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: ca0ed45ad3f274e6d7fa79734acfd6fabace9bf2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917948"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Inspecione as propriedades XAML durante a depuração
Você pode obter uma exibição em tempo real de seu código XAML em execução com o **Live Visual Tree** e o **Live Property Explorer**. Essas ferramentas oferecem um modo de exibição de árvore dos elementos da interface do usuário do seu aplicativo em execução do XAML e mostram as propriedades de tempo de execução de qualquer elemento de interface do usuário selecionado.  
  
 Você pode usar essas ferramentas nas seguintes configurações:  
  
|Tipo de aplicativo|Ferramentas e sistema operacional|  
|-----------------|--------------------------------|  
|Aplicativos de Windows Presentation Foundation (4.0 e acima)|Windows 7 e acima|  
|Aplicativos Universais do Windows|Windows 10 e acima, com o [Windows 10 SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Examinando os elementos na árvore Visual  
 Vamos começar com um aplicativo muito simples do WPF que tem uma exibição de lista e um botão. Sempre que você clica no botão, o outro item é adicionado à lista. Itens pares são coloridos em cinza e itens ímpares são coloridos de amarelos.  
  
 Criar um novo aplicativo do WPF em C# (arquivo > Novo > projeto, em seguida, selecione c# e localizar o aplicativo do WPF). Denomine **TestXAML**.  
  
 Altere o MainWindow. XAML para o seguinte:  
  
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
  
 Compile o projeto e comece a depuração. (A configuração de compilação deve ser Debug, em vez de lançar. Para saber mais sobre configurações de build, confira [Noções básicas sobre configurações de build](../ide/understanding-build-configurations.md).  
  
 Quando a janela é exibida, clique no **Adicionar Item** botão algumas vezes. Você deve ver algo parecido com isso:  
  
 ![Janela principal do aplicativo](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")  
  
 Agora, abra o **Live Visual Tree** janela (**Depurar > Windows > Live Visual Tree**, ou encontrá-lo no lado esquerdo do IDE). Arraste-a para fora de sua posição de encaixe para que possamos observar essa janela e o **Live propriedades** janela lado a lado. No **Live Visual Tree** janela, expanda o **ContentPresenter** nó. Ele deve conter nós para o botão e a caixa de listagem. Expanda a caixa de listagem (e, em seguida, o **ScrollContentPresenter** e o **ItemsPresenter**) para localizar a lista de itens de caixa. A janela deve ter esta aparência:  
  
 ![ListBoxItems na árvore Visual em tempo real](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree ListBoxItems")  
  
 Volte para a janela do aplicativo e adicione alguns itens. Você deve ver mais itens de caixa de lista aparecem na **Live Visual Tree**.  
  
 Agora vamos examinar as propriedades de um dos itens da caixa de lista. Selecione o primeiro item de caixa de lista na **Live Visual Tree** e clique no **Mostrar propriedades** ícone na barra de ferramentas. O **Live Property Explorer** deve aparecer. Observe que o **conteúdo** campo é "Item1" e o **plano de fundo** campo é **#ffffffe0** (amarelo claro). Volte para o **Live Visual Tree** e selecione o segundo item de caixa de listagem. O **Live Property Explorer** deve mostrar que o **conteúdo** campo é "Item2" e o **plano de fundo** campo é **#ffd3d3d3** (cinza-claro ).  
  
 A estrutura real do que o XAML tem vários elementos que você provavelmente não está interessado diretamente, e se você não souber o código também pode ter dificuldade para navegar pela árvore para localizar o que você está procurando. Portanto, o **Live Visual Tree** possui duas maneiras que permitem a você usar a interface do usuário do aplicativo para ajudá-lo a localizar o elemento que você deseja examinar.  
  
 **Habilitar seleção no aplicativo em execução**. Você pode habilitar esse modo quando você seleciona o botão mais à esquerda na **Live Visual Tree** barra de ferramentas. Com esse modo em, você pode selecionar um elemento de interface do usuário no aplicativo e o **Live Visual Tree** (e o **Visualizador de propriedade Live**) é atualizado automaticamente para mostrar o nó da árvore correspondente a esse elemento, e suas propriedades.  
  
 **Exibir adornos de layout no aplicativo em execução**. Você pode habilitar esse modo quando você seleciona o botão que está imediatamente à direita do botão de seleção Habilitar. Quando **exibir adornos de layout** estiver ativado, ele faz com que a janela do aplicativo mostrar as linhas horizontais e verticais ao longo dos limites do objeto selecionado para que você possa ver o que ele se alinhe com, bem como retângulos, mostrando as margens. Por exemplo, ativar ambos **habilitar a seleção** e **layout de exibição** ativado e selecione o **Add Item** bloco de texto no aplicativo. Você deve ver o nó de bloco de texto na **Live Visual Tree** e propriedades de bloco de texto na **Visualizador de propriedade Live**, bem como as linhas horizontais e verticais sobre os limites do bloco de texto.  
  
 ![LivePropertyViewer em DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer DisplayLayout")  
  
 **Visualizar Seleção**. Você pode habilitar esse modo, selecionando o terceiro botão da esquerda na barra de ferramentas Live Visual Tree. Esse modo mostra o XAML em que o elemento tiver sido declarado, se você tiver acesso ao código-fonte do aplicativo. Selecione **habilitar a seleção** e **visualizar seleção**, e, em seguida, selecione o botão no nosso aplicativo de teste. O arquivo de MainWindow. XAML é aberto no Visual Studio e o cursor é colocado na linha em que o botão é definido.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Usando ferramentas XAML com aplicativos em execução  
 Você pode usar essas ferramentas XAML, mesmo quando você não tiver o código-fonte. Quando você anexa a um aplicativo XAML em execução, você pode usar o **Live Visual Tree** nos elementos da interface do usuário de aplicativo muito. Aqui está um exemplo, com o mesmo aplicativo de teste do WPF usado anteriormente.  
  
1.  Iniciar o **TestXaml** aplicativo na configuração de versão. Você não pode anexar a um processo que está sendo executado em um **depurar** configuração.  
  
2.  Abra uma segunda instância do Visual Studio e clique em **Depurar > Anexar ao processo**. Encontre **TestXaml.exe** na lista de processos disponíveis e clique em **Attach**.  
  
3.  O aplicativo começa a ser executado.  
  
4.  Na segunda instância do Visual Studio, abra o **Live Visual Tree** (**Depurar > Windows > Live Visual Tree**). Você deve ver a **TestXaml** elementos de interface do usuário e você deve ser capaz de manipulá-los como você durante a depuração do aplicativo diretamente.