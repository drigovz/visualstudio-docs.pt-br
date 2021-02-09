---
title: Depuração histórica | Microsoft Docs
description: Solucionar problemas de um aplicativo inspecionando seu estado à medida que você retrocede e avança pela execução. O IntelliTrace coleta as informações para esse recurso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4a6bf07cc7905fc48bcc82c8b38fa5b6f6e7cfa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904415"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Depuração histórica (C#, Visual Basic, C++)

A depuração histórica é um modo de depuração que depende das informações coletadas pelo IntelliTrace. Ele permite que você se mova para trás e para frente pela execução do seu aplicativo e inspecione seu estado.

 Você pode usar o IntelliTrace no Visual Studio Enterprise Edition (mas não as edições Professional ou Community).

## <a name="why-use-historical-debugging"></a>Por que usar a depuração histórica?

 A definição de pontos de interrupção para localizar bugs pode ser um sórdida ou um problema de perda. Você define um ponto de interrupção próximo ao local em seu código em que você suspeita que o bug seja, execute o aplicativo no depurador e espero que o ponto de interrupção seja atingido e que o local em que a execução é interrompida possa revelar a origem do bug. Caso contrário, você precisará tentar definir um ponto de interrupção em outro lugar no código e executar novamente o depurador, executando as etapas de teste repetidamente até encontrar o problema.

 ![definindo um ponto de interrupção](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 Você pode usar o IntelliTrace e a depuração histórica para fazer o roaming em seu aplicativo e inspecionar seu estado (pilha de chamadas e variáveis locais) sem precisar definir pontos de interrupção, reiniciar a depuração e repetir etapas de teste. Isso pode poupar muito tempo, especialmente quando o bug está mais profundo em um cenário de teste que leva muito tempo para ser executado.

## <a name="how-do-i-start-using-historical-debugging"></a>Como fazer começar a usar a depuração histórica?

O IntelliTrace está ativado por padrão. Tudo o que você precisa fazer é decidir quais eventos e chamadas de função são de seu interesse e se deseja exibir instantâneos do estado completo do aplicativo. Para obter mais informações sobre como definir o que você deseja procurar, consulte [recursos do IntelliTrace](../debugger/intellitrace-features.md). O suporte a recursos varia de acordo com o tipo de aplicativo e de idioma.

- Para exibir instantâneos com depuração histórica, consulte [inspecionar os Estados de aplicativos anteriores usando o IntelliTrace](../debugger/view-historical-application-state.md)
- Para saber como inspecionar variáveis e navegar pelo código, consulte [inspecionar seu aplicativo com a depuração histórica](../debugger/historical-debugging-inspect-app.md)
- Para saber mais sobre depuração com eventos do IntelliTrace, consulte [instruções passo a passo: usando o IntelliTrace](../debugger/walkthrough-using-intellitrace.md).