---
title: Depurar violações de acesso ao executar o aplicativo fora do VS
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
ms.openlocfilehash: 94a905ad37bdfa42b17a54a34f6a1cde8e0b4e6e
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809525"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Como posso depurar violações de acesso ao executar meu programa fora do depurador?

## <a name="problem-description"></a>Descrição do problema
 Meu programa é executado corretamente no ambiente do Visual Studio, mas quando eu o executo em modo autônomo no sistema operacional Windows, ele gera uma violação de acesso. Como posso depurar esse problema?

## <a name="solution"></a>Solução
 Defina a opção [depuração Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md) e execute o programa autônomo, até que ocorra a violação de acesso. Em seguida, na caixa de diálogo **Violação de Acesso**, clique em **Cancelar** para iniciar o depurador.

## <a name="see-also"></a>Confira também
- [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)