---
title: 'Etapa 9: Experimentar outros recursos'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5af132efde0c1a49e5404fa602363aab0554e6f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572472"
---
# <a name="step-9-try-other-features"></a>Etapa 9: Experimentar outros recursos
Para aprender mais, tente alterar os ícones e as cores, adicionar um temporizador de jogo e adicionar sons. Para tornar o jogo mais desafiador, tente aumentar o tabuleiro e ajustar o temporizador.

Para baixar uma versão completa do exemplo, veja [Complete Matching Game tutorial sample (Exemplo de tutorial completo de jogo da memória)](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Para testar outros recursos

- Substitua os ícones e as cores pelos de sua preferência.

    > [!TIP]
    > Tente observar a propriedade [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) do rótulo.

- Adicione um temporizador de jogo que controla em quanto tempo o jogador ganha uma partida.

    > [!TIP]
    > Para isso, você pode adicionar um rótulo para exibir o tempo decorrido no formulário acima de <xref:System.Windows.Forms.TableLayoutPanel> e adicionar outro temporizador ao formulário para controlar o tempo. Use código para iniciar o temporizador quando o jogador começar o jogo e para interromper o temporizador depois que os dois últimos ícones forem encontrados.

- Adicione um som para quando o jogador encontrar um par, outro som para quando o jogador selecionar dois ícones que são diferentes e um terceiro som para quando o programa ocultar os ícones novamente.

    > [!TIP]
    > Para reproduzir sons, você pode usar o namespace <xref:System.Media>. Veja [Reproduzir sons no aplicativo Windows Forms (C#)](http://youtu.be/qOh4ooHg1UU) ou [Como reproduzir áudio no Visual Basic](http://youtu.be/-4oPDeQrtMs) para obter mais informações.

- Torne o jogo mais difícil aumentando o tamanho do tabuleiro.

    > [!TIP]
    > Você precisará fazer mais do que apenas adicionar linhas e colunas ao TableLayoutPanel – você também precisará considerar o número de ícones criados.

- Torne o jogo mais desafiador ocultando o primeiro ícone se o jogador demorar demais para reagir e não escolher o segundo ícone antes do término de um determinado tempo.

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Há recursos de aprendizagem por vídeo excelentes e gratuitos disponíveis para você. Para saber mais sobre programação no Visual Basic, veja [Visual Basic Fundamentals: Development for Absolute Beginners (Conceitos básicos do Visual Basic: desenvolvimento para iniciantes absolutos)](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Para saber mais sobre programação no C#, consulte [ C# conceitos básicos: desenvolvimento para iniciantes absolutos](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Para retornar à etapa anterior do tutorial, veja [Etapa 8: Adicionar um método para verificar se o jogador ganhou](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
