---
title: Usando as opções de acessibilidade do macOS
description: Usando recursos e opções de acessibilidade do macOS, como alto contraste, navegação de teclado e VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998380"
---
# <a name="accessibility-features-of-macos"></a>Recursos de acessibilidade do macOS

o macOS é um sistema operacional acessível, com vários recursos para ajudar os usuários de diferentes capacidades. Esses recursos incluem um modo de alto contraste, navegação por teclado e VoiceOver (o leitor de tela macOS).

## <a name="enable-accessibility-features"></a>Habilitar recursos de acessibilidade

No Visual Studio para Mac, o suporte para tecnologias assistenciais é desativado por padrão. Para habilitar o suporte de acessibilidade:

1. Vá para o **Visual Studio (menu)**  >  **preferências**  >  **outros** e selecione **acessibilidade**.

1. Marque a caixa de seleção **habilitar acessibilidade** .

   ![Captura de tela de preferências de acessibilidade, com habilitar acessibilidade selecionada](media/accessibility-preferences.png)

1. Selecione **reiniciar o Visual Studio** para habilitar o suporte para as tecnologias assistenciais da Apple.

Como alternativa, você pode usar a linha de comando para habilitar os recursos de acessibilidade. Para isso, digite o seguinte comando no terminal:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Depois de alterar essa configuração por meio da linha de comando, será necessário reiniciar o Visual Studio.

## <a name="increase-the-contrast-in-macos"></a>Aumentar o contraste no macOS

O Visual Studio para Mac dá suporte a aumentos de contraste no macOS, aumentando o contraste dos elementos da interface do usuário e tornando os contornos mais definidos. Para habilitar isso:

1. Abra as **preferências do sistema**.

1. Vá para **acessibilidade** e selecione **Exibir**.

1. Marque a caixa de seleção **aumentar contraste** .
