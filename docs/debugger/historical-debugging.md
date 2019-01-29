---
title: Histórico de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc16c6e6186d53bd08bd0634e07a4d1172859280
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54227246"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Histórico de depuração (C#, Visual Basic, C++)

Depuração de histórico é um modo de depuração que depende das informações coletadas pelo IntelliTrace. Ele permite que você voltar para encaminhar por meio da execução do seu aplicativo e inspecionar seu estado.  
  
 Você pode usar o IntelliTrace no Visual Studio Enterprise edition (mas não as edições Professional ou Community).  
  
## <a name="why-use-historical-debugging"></a>Por que usar o histórico de depuração?

 Definir pontos de interrupção para encontrar bugs pode ser uma questão em vez disso, tanto inexata. Você define um ponto de interrupção perto o lugar em seu código onde você suspeitar que o bug seja e executar o aplicativo no depurador e esperança de que seu ponto de interrupção obtém ocorrências e que o local em que a execução quebra pode revelar a origem do erro. Caso contrário, você terá que tente definir um ponto de interrupção em outro lugar no código e execute novamente o depurador, executando as etapas de teste repetidamente até encontrar o problema.  
  
 ![definindo um ponto de interrupção](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Você pode usar o IntelliTrace e a depuração histórica circulem por em seu aplicativo e inspecionar o estado (pilha de chamadas e variáveis locais) sem precisar definir pontos de interrupção, reinicie a depuração e repita as etapas de teste. Isso pode economizar muito tempo, especialmente quando o bug estiver localizado profundo em um cenário de teste que leva muito tempo para ser executado.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Como posso começar a usar a depuração de histórico?

 IntelliTrace está ativado por padrão. Tudo o que você precisa fazer é decidir quais eventos e chamadas de função são interessantes para você, e se você deseja exibir instantâneos do estado completo do aplicativo. Para obter mais informações sobre como definir o que você deseja procurar, consulte [recursos do IntelliTrace](../debugger/intellitrace-features.md). Suporte a recursos varia por idioma e o aplicativo de tipo.

 - Para exibir instantâneos de histórico de depuração, consulte [inspecionar estados anteriores do aplicativo usando o IntelliTrace](../debugger/view-historical-application-state.md)
 - Para aprender a inspecionar variáveis e navegar no código, consulte [inspecionar seu aplicativo com o histórico de depuração](../debugger/historical-debugging-inspect-app.md)
 - Para saber mais sobre depuração com eventos do IntelliTrace, consulte [instruções passo a passo: usando o IntelliTrace](../debugger/walkthrough-using-intellitrace.md).