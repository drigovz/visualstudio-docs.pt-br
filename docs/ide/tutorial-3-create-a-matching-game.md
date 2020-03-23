---
title: 'Tutorial 3: Criar um jogo da memória'
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 619c21f4878f2e421ee5ac5ea76a68cd6e6bc337
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579711"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutorial 3: Criar um jogo da memória

Neste tutorial, você cria um jogo da memória, onde o jogador deve combinar pares de ícones ocultos.

> [!NOTE]
> Este tutorial abrange tanto C# quanto Visual Basic, então concentre-se nas informações específicas da linguagem de programação que você está usando.

Este tutorial orienta você sobre as seguintes tarefas:

- Armazenar objetos, como ícones, em um objeto <xref:System.Collections.Generic.List%601>.

- Use `foreach` um loop em `For Each` C# ou um loop no Visual Basic para iterar através de itens em uma lista.

- Acompanhar o estado de um formulário usando variáveis de referência.

- Criar um manipulador de eventos para responder a eventos que você pode usar com vários objetos.

- Criar um temporizador que faça a contagem regressiva e dispare um evento logo depois que ele for iniciado.

Quando você terminar, seu aplicativo deve ser semelhante à seguinte imagem:

![Jogo que você cria neste tutorial](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Links do tutorial

|Title|Descrição|
|-----------|-----------------|
|[Etapa 1: Criar um projeto e adicionar uma tabela ao formulário](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Comece criando o projeto e adicionando um controle `TableLayoutPanel` para manter os controles devidamente alinhados.|
|[Passo 2: Adicione um objeto aleatório e uma lista de ícones](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Adicione um objeto `Random` e um objeto `List` para criar uma lista de ícones.|
|[Etapa 3: Atribuir um ícone aleatório a cada rótulo](../ide/step-3-assign-a-random-icon-to-each-label.md)|Atribua os ícones aleatoriamente aos controles `Label` para que cada jogo seja diferente.|
|[Passo 4: Adicione um manipulador de eventos de clique a cada rótulo](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Adicione um manipulador de eventos `Click` que altere a cor do rótulo que é clicado.|
|[Etapa 5: Adicionar referências de rótulo](../ide/step-5-add-label-references.md)|Adicione variáveis de referência para acompanhar quais rótulos são clicados.|
|[Etapa 6: Adicionar um temporizador](../ide/step-6-add-a-timer.md)|Adicione um temporizador ao formulário para controlar o tempo que passou no jogo.|
|[Etapa 7: Manter os pares visíveis](../ide/step-7-keep-pairs-visible.md)|Mantenha pares de ícones visíveis, se um par correspondente for selecionado.|
|[Passo 8: Adicione um método para verificar se o jogador ganhou](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Adicione um método `CheckForWinner()` para verificar se o jogador venceu.|
|[Etapa 9: Experimentar outros recursos](../ide/step-9-try-other-features.md)|Teste outros recursos, como alterar ícones e cores, adicionar uma grade e adicionar sons. Tente aumentar o tamanho do tabuleiro e ajustar o temporizador.|

Há também ótimos recursos gratuitos de aprendizagem de vídeo disponíveis para você. Para saber mais sobre programação em C#, consulte [c# fundamentos: Desenvolvimento para iniciantes absolutos](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Para saber mais sobre programação no Visual Basic, veja [Visual Basic Fundamentals: Development for Absolute Beginners (Conceitos básicos do Visual Basic: desenvolvimento para iniciantes absolutos)](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Próximas etapas

Para começar o tutorial, comece com **[o Passo 1: Crie um projeto e adicione uma tabela ao seu formulário](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)**.

## <a name="see-also"></a>Confira também

* [Mais tutoriais C#](/visualstudio/get-started/csharp/)
* [Tutoriais sobre Visual Basic](/visualstudio/get-started/visual-basic/)
* [Tutoriais c++](/cpp/get-started/tutorial-console-cpp)
