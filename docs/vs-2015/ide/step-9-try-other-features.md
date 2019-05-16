---
title: 'Etapa 9: Experimentar outros recursos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 495d98f4061c258c78b2b74929428aec4eb3ec0c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65678935"
---
# <a name="step-9-try-other-features"></a>Etapa 9: Experimentar outros recursos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para aprender mais, tente alterar os ícones e as cores, adicionar um temporizador de jogo e adicionar sons. Para tornar o jogo mais desafiador, tente aumentar o tabuleiro e ajustar o temporizador.  
  
 Para baixar uma versão completa do exemplo, consulte [Complete Matching Game tutorial sample (Exemplo de tutorial completo de jogo da memória)](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
### <a name="to-try-other-features"></a>Para testar outros recursos  
  
- Substitua os ícones e as cores pelos de sua preferência.  
  
    > [!TIP]
    > Tente observar a propriedade [Forecolor](https://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) do rótulo.  
  
- Adicione um temporizador de jogo que controla em quanto tempo o jogador ganha uma partida.  
  
    > [!TIP]
    > Para isso, você pode adicionar um rótulo para exibir o tempo decorrido no formulário acima de TableLayoutPanel e adicionar outro temporizador ao formulário para controlar o tempo. Use código para iniciar o temporizador quando o jogador começar o jogo e para interromper o temporizador depois que os dois últimos ícones forem encontrados.  
  
- Adicione um som para quando o jogador encontrar um par, outro som para quando o jogador selecionar dois ícones que são diferentes e um terceiro som para quando o programa ocultar os ícones novamente.  
  
    > [!TIP]
    > Para reproduzir sons, você pode usar o namespace System.media. Consulte [Reproduzir sons no aplicativo Windows Forms (C# .NET)](http://youtu.be/qOh4ooHg1UU) ou [Como reproduzir áudio no Visual Basic](http://youtu.be/-4oPDeQrtMs) para obter mais informações.  
  
- Torne o jogo mais difícil aumentando o tamanho do tabuleiro.  
  
    > [!TIP]
    > Você precisará fazer mais do que apenas adicionar linhas e colunas ao TableLayoutPanel; você também precisará considerar o número de ícones criados.  
  
- Torne o jogo mais desafiador ocultando o primeiro ícone se o jogador demorar demais para reagir e não escolher o segundo ícone antes do término de um determinado tempo.  
  
### <a name="to-continue-or-review"></a>Para continuar ou revisar  
  
- Se você estiver com dificuldades ou tiver dúvidas quanto à programação, tente publicar sua dúvida em um dos fóruns do MSDN. Consulte [Fórum do Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) e [Fórum do Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
- Há recursos de aprendizagem por vídeo excelentes e gratuitos disponíveis para você. Para saber mais sobre programação no Visual Basic, consulte [fundamentos do Visual Basic: Desenvolvimento para iniciantes absolutos](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Para saber mais sobre programação no Visual c#, consulte [conceitos básicos do c#: Desenvolvimento para iniciantes absolutos](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
- Para retornar à etapa anterior do tutorial, confira [Etapa 8: Adicione um método para verificar se o jogador ganhou](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
