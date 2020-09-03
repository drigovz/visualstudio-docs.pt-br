---
title: Organizar objetos em contêineres de layout no XAML Designer
ms.date: 07/17/2020
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ebe96ec84d957c5ac8dcb6bad0a388ba3318c0fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86459288"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organizar objetos em contêineres de layout no XAML Designer

Este artigo descreve os controles e painéis de layout do Designer XAML.

Imagine o local em que deseja que os objetos apareçam em uma página&mdash;como imagens, botões e vídeos. Talvez você queira que eles apareçam em linhas e colunas; em uma única linha, vertical ou horizontal; ou em posições fixas.

Depois de pensar como a página pode ser exibida, escolha um painel de layout. Todas as páginas começam com um, porque você precisa de algo ao qual adicionar os objetos. Por padrão, ele é uma **Grade**, mas você pode alterá-lo.

Painéis de layout ajudam a organizar objetos em uma página, mas fazem mais do que isso. Eles ajudam a projetar diferentes tamanhos de tela e resoluções. Quando usuários executam um aplicativo, tudo o que está contido no painel de layout é redimensionado para caber na tela do dispositivo em uso. É claro que, se você não quiser que isso aconteça com o layout, será possível substituir esse comportamento em uma parte ou na totalidade do layout. É possível usar propriedades de altura e largura para controlar isso.

## <a name="layout-panels"></a>Painéis de layout

Comece a página escolhendo um destes painéis de layout. A página pode ter mais de um. Por exemplo, é possível iniciar com um painel de layout em **Grade** e, em seguida, adicionar um **StackPanel** a uma área na **Grade** para organizar os controles verticalmente nesse elemento.

Os painéis de layout a seguir são os mais populares, mas existem outros. Você pode encontrá-los todos na **Caixa de ferramentas** no Visual Studio ou no painel **Ativos** no Blend para Visual Studio.

### <a name="grid"></a>Grade

Organize objetos em linhas e colunas.

![Painel de layout de grade](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Organize objetos em regiões de grade iguais ou uniformes. Este painel é ótimo para organizar uma lista de imagens.

(Disponível somente para projetos WPF.)

![Painel de layout UniformGrid](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

### <a name="canvas"></a>Canvas

Organize objetos como desejar. Quando os usuários executam o aplicativo, esses elementos terão posições fixas na tela.

![Painel de layout de tela](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Organize objetos em uma única linha horizontal ou vertical.

![Painel de layout StackPanel](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Organize objetos em sequência da esquerda para a direita. Quando o painel fica sem espaço na margem à direita, ele *encapsula* o conteúdo na próxima linha e assim por diante, da esquerda para a direita, de cima para baixo. A orientação de um painel de encapsulamento também pode ser vertical, para que os objetos sejam direcionados de cima para baixo e da esquerda para a direita.

(Disponível somente para projetos WPF.)

![Painel de layout WrapPanel](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Organize objetos para que eles fiquem ou se *encaixem*, em uma borda do painel.

(Disponível somente para projetos WPF.)

![Painel de layout DockPanel](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Assista a um vídeo curto:** ![botão Reproduzir](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF – DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Controles de layout

Também é possível adicionar objetos aos controles de layout. Eles não têm tantos recursos como o painel de layout, mas podem ser úteis em determinados cenários.

Os controles de layout a seguir são os mais populares, mas existem outros. Você pode encontrá-los todos na **Caixa de ferramentas** no Visual Studio ou no painel **Ativos** no Blend para Visual Studio.

### <a name="border"></a>Borda

Crie uma borda, uma tela de fundo ou ambos em torno de um objeto. É possível adicionar apenas um objeto a uma **Borda**. Caso queira aplicar uma borda ou tela de fundo a mais de um objeto, adicione o painel de layout à **Borda**. Em seguida, adicione objetos a esse painel ou controle.

![Controle de layout de borda](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Pop-up

Mostra informações ou opções para usuários em uma janela. É possível adicionar apenas um objeto a um **Pop-up**. Por padrão, um **Pop-up** contém uma **Grade**, mas isso pode ser alterado.

### <a name="scrollviewer"></a>ScrollViewer

Permite aos usuários rolar para baixo uma página ou uma área dela. É possível adicionar apenas um objeto a um **ScrollViewer**, por isso, faz sentido adicionar um painel de layout como uma **Grade** ou **StackPanel**.

![Controle de layout ScrollViewer](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

Dimensionar objetos, assim como um controle de zoom. É possível adicionar apenas um objeto a uma **Caixa de Visualização**. Caso deseje aplicar esse efeito a mais de um objeto, adicione um painel de layout à **Caixa de Visualização** e, em seguida, adicione os controles a esse painel de layout.

![Controle de layout ViewBox](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Confira também

- [Trabalhar com elementos no Designer XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Criar uma interface do usuário usando o Designer XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
