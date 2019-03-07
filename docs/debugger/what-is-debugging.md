---
title: O que é depuração?
description: Entender o que significa depurar um aplicativo
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c01317f3b8fa92cf1bc17c3745f708e0d3f26e5b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919324"
---
# <a name="what-is-debugging"></a>O que é depuração?

O depurador do Visual Studio é uma ferramenta poderosa. Antes de mostrarmos como usá-lo, queremos falar sobre alguns termos como *depurador*, *depuração*, e *modo de depuração*. Dessa forma, quando falamos posteriormente encontrando e corrigindo bugs, vamos falar sobre a mesma coisa.

## <a name="debugger-vs-debugging"></a>O depurador vs. a depuração

O termo *depuração* pode significar muitas coisas diferentes, mas mais literalmente, significa a remoção de bugs do seu código. Agora, há muitas maneiras de fazer isso. Por exemplo, você pode depurar examinando seu código procurando por erros de digitação ou usando um analisador de código. Você pode depurar o código usando um criador de perfil de desempenho. Ou, você pode depurar usando um *depurador*.

Um depurador é uma ferramenta de desenvolvedor muito especializados que anexa ao seu aplicativo em execução e permite que você inspecione o seu código. Na documentação de depuração para o Visual Studio, isso normalmente é o que queremos dizer quando dizemos "depuração".

## <a name="debug-mode-vs-running-your-app"></a>Modo versus que executam seu aplicativo de depuração

Quando você executa seu aplicativo no Visual Studio pela primeira vez, você pode iniciá-lo pressionando o botão de seta verde ![iniciar depuração](../debugger/media/dbg-tour-start-debugging.png "iniciar depuração") na barra de ferramentas (ou **F5**). Por padrão, o **depurar** valor aparece na lista suspensa à esquerda. Se você for novo no Visual Studio, isso pode deixar a impressão que depurar seu aplicativo tem algo a ver com a execução de seu aplicativo, que ele faz – mas eles são basicamente duas tarefas muito diferentes.

![Selecione uma compilação de depuração](../debugger/media/what-is-debugging-debug-build.png)

Um **depurar** valor indica que uma configuração de depuração. Quando você inicia o aplicativo (pressione a seta verde ou **F5**) em uma configuração de depuração, você deve iniciar o aplicativo no *modo de depuração*, que significa que você estiver executando seu aplicativo com o depurador anexado. Isso permite que um conjunto completo de funcionalidades de depuração que você pode usar para ajudar a encontrar bugs em seu aplicativo.

Se você tiver um projeto aberto, escolha o seletor de lista suspensa onde diz **Debug** e escolha **versão** em vez disso.

![Selecione uma compilação de versão](../debugger/media/what-is-debugging-release-build.png)

Quando você alternar essa configuração, você alterar seu projeto de uma configuração de depuração para uma configuração de versão. Projetos do Visual Studio tem a versão separada e configurações para o seu programa de depuração. Você compila a versão de depuração para depuração e a versão de lançamento para a distribuição da versão final. Um build de versão é otimizado para desempenho, mas um build de depuração é melhor para depuração.

## <a name="when-to-use-a-debugger"></a>Quando usar um depurador

O depurador é uma ferramenta essencial para encontrar e corrigir bugs em seus aplicativos. No entanto, o contexto é king e é importante aproveitar todas as ferramentas em seu disposable para ajudar a eliminar rapidamente bugs ou erros. Às vezes, o direito de "tool" pode ser uma prática de codificação melhores. Aprendendo quando usar o depurador vs. de alguma outra ferramenta, você também aprenderá a usar o depurador com mais eficiência.

## <a name="next-steps"></a>Próximas etapas

Neste artigo, você aprendeu alguns conceitos gerais de depuração. Em seguida, você pode começar a aprender como depurar com o Visual Studio e como escrever código com menos bugs. Mostrar os artigos a seguir C# exemplos de código, mas os conceitos se aplicam a todos os idiomas com suporte do Visual Studio.

> [!div class="nextstepaction"]
> [Depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Ferramentas e técnicas de depuração](../debugger/write-better-code-with-visual-studio.md)
