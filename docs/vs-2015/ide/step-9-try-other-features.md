---
title: 'Etapa 9: Experimentar outros recursos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 379fc9c28b8d36f7bd606719a443b16108f0095d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299976"
---
# <a name="step-9-try-other-features"></a>Etapa 9: Experimentar outras funcionalidades
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para aprender mais, tente alterar os ícones e as cores, adicionar um temporizador de jogo e adicionar sons. Para tornar o jogo mais desafiador, tente aumentar o tabuleiro e ajustar o temporizador.

### <a name="to-try-other-features"></a>Para testar outros recursos

- Substitua os ícones e as cores pelos de sua preferência.

    > [!TIP]
    > Tente observar a propriedade [Forecolor](https://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) do rótulo.

- Adicione um temporizador de jogo que controla em quanto tempo o jogador ganha uma partida.

    > [!TIP]
    > Para isso, você pode adicionar um rótulo para exibir o tempo decorrido no formulário acima de TableLayoutPanel e adicionar outro temporizador ao formulário para controlar o tempo. Use código para iniciar o temporizador quando o jogador começar o jogo e para interromper o temporizador depois que os dois últimos ícones forem encontrados.

- Adicione um som para quando o jogador encontrar um par, outro som para quando o jogador selecionar dois ícones que são diferentes e um terceiro som para quando o programa ocultar os ícones novamente.

    > [!TIP]
    > Para reproduzir sons, você pode usar o namespace System.media. Consulte [Reproduzir sons no aplicativo Windows Forms (C# .NET)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) ou [Como reproduzir áudio no Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) para obter mais informações.

- Torne o jogo mais difícil aumentando o tamanho do tabuleiro.

    > [!TIP]
    > Você precisará fazer mais do que apenas adicionar linhas e colunas ao TableLayoutPanel; você também precisará considerar o número de ícones criados.

- Torne o jogo mais desafiador ocultando o primeiro ícone se o jogador demorar demais para reagir e não escolher o segundo ícone antes do término de um determinado tempo.

### <a name="to-continue-or-review"></a>Para continuar ou revisar

- Se você estiver com dificuldades ou tiver dúvidas quanto à programação, tente publicar sua dúvida em um dos fóruns do MSDN. Consulte [Fórum do Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) e [Fórum do Visual C#](https://social.msdn.microsoft.com/Forums/en-US/home).

- Há recursos de aprendizagem por vídeo excelentes e gratuitos disponíveis para você. Para saber mais sobre programação em Visual Basic, consulte [conceitos básicos de Visual Basic: desenvolvimento para iniciantes absolutos](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Para saber mais sobre programação no Visual C#, consulte [C# Fundamentals: Development for Absolute Beginners (Conceitos básicos do C#: desenvolvimento para iniciantes absolutos)](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Para retornar à etapa anterior do tutorial, consulte [etapa 8: adicionar um método para verificar se o jogador venceu](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
