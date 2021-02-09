---
title: Caixa de diálogo quando o ponto de interrupção é atingido | Microsoft Docs
description: Use quando o ponto de interrupção for atingido para especificar uma ação na interrupção. Você pode especificar que uma mensagem seja impressa e que a execução deve continuar depois.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfb5099bd0fab17cd983af4e16a435fd192a1668
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883864"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Caixa de diálogo Ponto de Interrupção Quando Visitado
Com essa caixa de diálogo, você pode personalizar a ação que ocorre quando um ponto de interrupção é atingido.

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Imprimir uma mensagem** Imprime uma mensagem usando a sintaxe DebuggerDisplay. Para obter mais informações, consulte [usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Essa caixa de texto também oferece suporte à palavras-chave especiais (como $ADDRESS) que podem ser usadas por si mesmas ou nas chaves de uma expressão do DebuggerDisplay. As palavras-chave disponíveis são listadas na caixa de diálogo.

 **Continuar execução** Esse controle é habilitado somente quando **a impressão de uma mensagem** é selecionada. Com esse controle selecionado, você pode usar um ponto de interrupção como um tracepoint para rastrear a execução do programa, em vez de interrompê-lo quando o local for atingido.

## <a name="see-also"></a>Confira também
- [Usando pontos de interrupção](../debugger/using-breakpoints.md)
- [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)