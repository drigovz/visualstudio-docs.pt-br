---
title: Usar janelas do depurador durante a depuração de um aplicativo em primeiro plano | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11bd61cda8c92721fb42c640b0b5100b8054acdf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698021"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Como posso usar janelas do depurador durante a depuração de um programa em primeiro plano?
## <a name="problem-description"></a>Descrição do problema
 Estou tentando depurar um problema de pintura em tela. Para observar esse problema, tenho que manter o programa no primeiro plano, o que significa que não tenho acesso às janelas de depuração. O que posso fazer?

## <a name="solution"></a>Solução
 Se você tiver um segundo computador, poderá usar a depuração remota. Com uma configuração de dois computadores, você poderá ver a pintura da tela no computador remoto quando operar o depurador no host. Para obter mais informações sobre a depuração remota, consulte [depuração remota](../debugger/remote-debugging.md).

## <a name="see-also"></a>Consulte também
- [Perguntas frequentes de depuração de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)