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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3435b7a270d89dc38f5ff10a1350418a24f91c0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883929"
---
# <a name="what-is-debugging"></a>O que é depuração?

O depurador do Visual Studio é uma ferramenta poderosa. Antes de mostrarmos como usá-lo, queremos falar sobre alguns termos, como *depurador*, *depuração* e modo de *depuração*. Dessa forma, quando falarmos mais tarde sobre a localização e a correção de bugs, falaremos sobre a mesma coisa.

## <a name="debugger-vs-debugging"></a>Depurador x depuração

O termo *depuração* pode significar muitas coisas diferentes, mas, na maioria das vezes, significa remover bugs do seu código. Agora, há muitas maneiras de fazer isso. Por exemplo, você pode depurar verificando seu código procurando erros de grafia ou usando um analisador de código. Você pode depurar o código usando um criador de perfil de desempenho. Ou você pode depurar usando um *depurador*.

Um depurador é uma ferramenta de desenvolvedor muito especializada que é anexada ao seu aplicativo em execução e permite que você inspecione seu código. Na documentação de depuração do Visual Studio, isso normalmente é o que queremos dizer quando dizemos "Debugging".

## <a name="debug-mode-vs-running-your-app"></a>Modo de depuração vs. executando seu aplicativo

Ao executar seu aplicativo no Visual Studio pela primeira vez, você pode iniciá-lo pressionando o botão de seta verde ![iniciar a depuração](../debugger/media/dbg-tour-start-debugging.png "Iniciar Depuração") na barra de ferramentas (ou **F5**). Por padrão, o valor de **depuração** é exibido na lista suspensa à esquerda. Se você for novo no Visual Studio, isso poderá deixar a impressão de que a depuração do seu aplicativo tem algo a ver com a execução do seu aplicativo – o que ele faz – mas essas são fundamentalmente duas tarefas muito diferentes.

![Selecionar uma compilação de depuração](../debugger/media/what-is-debugging-debug-build.png)

Um valor de **depuração** indica uma configuração de depuração. Ao iniciar o aplicativo (pressione a seta verde ou **F5**) em uma configuração de depuração, você inicia o aplicativo no *modo de depuração*, o que significa que você está executando seu aplicativo com um depurador anexado. Isso permite um conjunto completo de recursos de depuração que você pode usar para ajudar a encontrar bugs em seu aplicativo.

Se você tiver um projeto aberto, escolha o seletor suspenso onde ele diz **depurar** e escolha **liberar** , em vez disso.

![Selecionar uma compilação de versão](../debugger/media/what-is-debugging-release-build.png)

Ao alternar essa configuração, você altera o projeto de uma configuração de depuração para uma configuração de versão. Os projetos do Visual Studio têm configurações separadas de versão e depuração para seu programa. Você cria a versão de depuração para depuração e a versão de lançamento para a distribuição de versão final. Uma compilação de versão é otimizada para desempenho, mas uma compilação de depuração é melhor para depuração.

## <a name="when-to-use-a-debugger"></a>Quando usar um depurador

O depurador é uma ferramenta essencial para localizar e corrigir bugs em seus aplicativos. No entanto, o contexto é King, e é importante aproveitar todas as ferramentas à sua descartar para ajudá-lo a eliminar rapidamente bugs ou erros. Às vezes, a "ferramenta" certa pode ser uma prática de codificação melhor. Ao aprender quando usar o depurador versus alguma outra ferramenta, você também aprenderá a usar o depurador com mais eficiência.

## <a name="next-steps"></a>Próximas etapas

Neste artigo, você aprendeu alguns conceitos gerais de depuração. Em seguida, você pode começar a aprender a depurar com o Visual Studio e a escrever código com menos bugs. Os artigos a seguir mostram exemplos de código em C#, mas os conceitos se aplicam a todos os idiomas com suporte do Visual Studio.

> [!div class="nextstepaction"]
> [Depuração para iniciantes absolutos](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Técnicas e ferramentas de depuração](../debugger/write-better-code-with-visual-studio.md)
