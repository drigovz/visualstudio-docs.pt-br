---
title: Acessibilidade
description: Este artigo apresenta as funcionalidades de acessibilidade do Visual Studio para Mac e como elas podem ser habilitadas.
author: conceptdev
ms.author: crdun
ms.date: 04/17/2019
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 0ee6ffc7bd1567a86bc361f55e00c52ccecddd61
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824442"
---
# <a name="accessibility"></a>Acessibilidade

O Visual Studio para Mac tem os seguintes recursos de acessibilidade, tornando-o mais acessível para pessoas com diferentes capacidades:

- Ampliação de texto nos painéis editor e de soluções
- Opções de tamanho de texto em editores
- Personalização de cor em editores
- Navegação por teclado
- Personalização de atalhos
- Preenchimento de código para métodos e parâmetros

Além desses recursos, a Apple fornece várias ferramentas para auxiliar usuários com necessidades especiais, como VoiceOver e Ditado.

Para obter mais informações sobre recursos de acessibilidade no macOS, confira o [site da Apple](https://www.apple.com/accessibility/mac/).

## <a name="enabling-macos-assistive-technologies-in-visual-studio-for-mac"></a>Habilitação das Tecnologias Adaptativas do macOS no Visual Studio para Mac

O suporte do Visual Studio para Mac para tecnologias adaptativas do macOS está desativado por padrão. Para ativá-lo, siga estas etapas:

1. Acesse **Visual Studio (menu) > Preferências > Outros > Acessibilidade**

2. Marque a caixa de seleção **Habilitar acessibilidade**:

   ![Caixa de seleção de acessibilidade de preferências](media/accessibility-preferences.png)

3. Selecione o botão **Reiniciar o Visual Studio** para reiniciar o Visual Studio e habilitar o suporte para tecnologias adaptativas da Apple.

## <a name="how-to-use-keyboard-navigation"></a>Como: Usar a navegação por teclado

O suporte à navegação por teclado está integrado diretamente no macOS, mas para ter a experiência mais abrangente você deve configurar o macOS para navegar **Todos os controles**:

![Todos os controles do teclado de preferências do sistema](media/accessibility-preferences-keyboard.png)

Definir o **Acesso completo por teclado** para **Todos os controles** permite que você navegue por todos os controles em uma janela ou caixa de diálogo. Em seguida, você pode selecionar os controles usando:

- A tecla Tab para avançar pelos controles
- Shift-Tab para voltar pelos controles
- Teclas de direção para navegar entre os controles na direção das setas
- Control-Tab fora das caixas de área de texto
- Pressionar a Barra de espaço ativa o controle em foco no momento.

## <a name="how-to-enable-and-use-voiceover"></a>Como: Habilitar e usar o VoiceOver

Para habilitar ou desabilitar o VoiceOver pressione **&#8984; + F5**

Os comandos de VoiceOver aparecem neste guia como **VO + *tecla***, em que **VO** se refere ao modificador definido no aplicativo **VoiceOver Utility**. O modificador padrão é **Ctrl + Alt**. Por exemplo, dependendo do seu modificador de VoiceOver **VO + M** significará **Ctrl + Alt + M**. Para resumir, as teclas de cursor serão referidas como **Esquerda** e **Direita**, etc.

Para navegar na interface de usuário do Visual Studio para Mac, use as seguintes combinações de teclas:

- **VO + Direita/Esquerda**: navegar entre os elementos da interface do usuário
  - O VoiceOver anunciará o rótulo e o tipo de controle e explicará como interagir com ele.
- **VO + Shift + Para baixo/Para cima**: entra/sai de um elemento
  - Depois de entrar no elemento, você pode usar **VO + Esquerda/Direita** para navegar pelos elementos dentro dele.
- **VO + Barra de espaço**: selecionar/interagir com um controle
- **VO + M**: interagir com a barra de menus do Visual Studio para Mac

Confira mais informações sobre como usar o VoiceOver e uma lista abrangente dos comandos nos guias a seguir:

- [Guia de Introdução do VoiceOver da Apple](https://support.apple.com/en-us/guide/voiceover-guide/welcome/web)
- [Comandos de VoiceOver no macOS](http://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Consulte também

- [Recursos de acessibilidade do Visual Studio (no Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)
