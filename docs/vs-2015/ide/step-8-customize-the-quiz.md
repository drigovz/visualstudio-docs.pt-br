---
title: 'Etapa 8: personalizar o teste | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ded65e85a2ae11e96c21fdd852ea12daa4bbcdf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299992"
---
# <a name="step-8-customize-the-quiz"></a>Etapa 8: Personalizar o teste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na última parte do tutorial, você explorará algumas maneiras de personalizar o questionário e expandir no que já aprendeu. Por exemplo, pense em como o programa cria os problemas aleatórios de divisão para os quais a resposta nunca é uma fração. Para obter mais informações, mude o controle `timeLabel` para uma cor diferente e dê uma dica à pessoa realizando o teste.

### <a name="to-customize-the-quiz"></a>Para personalizar o teste

- Quando apenas cinco segundos restarem em um teste, defina o controle **timeLabel** como vermelho configurando sua propriedade **BackColor** (`timeLabel.BackColor = Color.Red;`). Redefina a cor quando o teste acabar.

- Dê ao comprador de teste uma dica executando um som quando a resposta correta for inserida em um controle NumericUpDown. (Você deve escrever um manipulador de eventos para o evento `ValueChanged()` de cada controle, que será acionado sempre que o comprador de teste alterar o valor do controle.)

### <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para o próximo tutorial, consulte [Tutorial 3: criar um jogo de correspondência](../ide/tutorial-3-create-a-matching-game.md).

- Para retornar à etapa anterior do tutorial, consulte [Etapa 7: adicionar problemas de multiplicação e divisão](../ide/step-7-add-multiplication-and-division-problems.md).
