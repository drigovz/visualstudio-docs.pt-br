---
title: Quando o ponto de interrupção é a caixa de diálogo ocorrências | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53f27b400c96f6b4336339e8d1beeec0dd87277c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944742"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Caixa de diálogo Ponto de Interrupção Quando Visitado
Com essa caixa de diálogo, você pode personalizar a ação que ocorre quando um ponto de interrupção é atingido.  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Imprimir uma mensagem**  
 Imprime uma mensagem, usando a sintaxe do DebuggerDisplay. Para obter mais informações, consulte [usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Essa caixa de texto também oferece suporte à palavras-chave especiais (como $ADDRESS) que podem ser usadas por si mesmas ou nas chaves de uma expressão do DebuggerDisplay. As palavras-chave disponíveis são listadas na caixa de diálogo.  
  
 **Continuar a execução**  
 Esse controle só será habilitado quando **Imprimir uma mensagem** for selecionado. Com esse controle selecionado, você pode usar um ponto de interrupção como um tracepoint para rastrear a execução do programa, em vez de interrompê-lo quando o local for atingido.  
  
## <a name="see-also"></a>Consulte também  
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)   
 [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)