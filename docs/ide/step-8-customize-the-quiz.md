---
title: 'Etapa 8: Personalizar o teste'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 168c86ace7fde9a2d354b4e9089b386f5cd876c6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970043"
---
# <a name="step-8-customize-the-quiz"></a>Etapa 8: Personalizar o teste
Na última parte do tutorial, você explorará algumas maneiras de personalizar o questionário e expandir no que já aprendeu. Por exemplo, pense em como o programa cria os problemas aleatórios de divisão para os quais a resposta nunca é uma fração. Para obter mais informações, mude o controle `timeLabel` para uma cor diferente e dê uma dica à pessoa realizando o teste.

## <a name="to-customize-the-quiz"></a>Para personalizar o teste

-   Quando apenas cinco segundos restarem em um teste, defina o controle **timeLabel** como vermelho configurando sua propriedade **BackColor** (`timeLabel.BackColor = Color.Red;`). Redefina a cor quando o teste acabar.

-   Dê ao comprador de teste uma dica executando um som quando a resposta correta for inserida em um controle <xref:System.Windows.Forms.NumericUpDown>. (Você deve escrever um manipulador de eventos para o evento <xref:System.Windows.Forms.NumericUpDown.ValueChanged> de cada controle, que será acionado sempre que o comprador de teste alterar o valor do controle.)

## <a name="to-continue-or-review"></a>Para continuar ou revisar

-   Para baixar uma versão concluída do teste, veja [Exemplo de tutorial de teste completo de matemática](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

-   Para passar para o próximo tutorial, confira [Tutorial 3: Criar um jogo da memória](../ide/tutorial-3-create-a-matching-game.md).

-   Para retornar à etapa anterior do tutorial, confira [Etapa 7: Adicionar problemas de multiplicação e divisão](../ide/step-7-add-multiplication-and-division-problems.md).
