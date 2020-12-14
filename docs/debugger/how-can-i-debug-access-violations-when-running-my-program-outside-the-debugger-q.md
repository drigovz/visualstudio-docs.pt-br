---
title: Depurar violações de acesso ao executar o aplicativo fora do Visual Studio
titleSuffix: ''
description: Use o depurador just-in-time para depurar uma violação de acesso que ocorra fora do ambiente do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49d1fb2b24488692031c647139aa1f1076f0dd6f
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398478"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Como posso depurar violações de acesso ao executar meu programa fora do depurador?

## <a name="problem-description"></a>Descrição do problema
 Meu programa é executado corretamente no ambiente do Visual Studio, mas quando eu o executo em modo autônomo no sistema operacional Windows, ele gera uma violação de acesso. Como posso depurar esse problema?

## <a name="solution"></a>Solução
 Defina a opção [depuração Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md) e execute o programa autônomo, até que ocorra a violação de acesso. Em seguida, na caixa de diálogo **Violação de Acesso**, clique em **Cancelar** para iniciar o depurador.

## <a name="see-also"></a>Consulte também
- [Perguntas frequentes sobre depuração de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)