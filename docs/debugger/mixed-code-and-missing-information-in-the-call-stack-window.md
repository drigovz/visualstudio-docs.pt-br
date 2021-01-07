---
title: Código misto & informações ausentes na janela pilha de chamadas
description: Em programas de modo misto (nativos e gerenciados), o depurador nem sempre pode mostrar a pilha de chamadas completa. Aprenda as possíveis discrepâncias quando o código nativo chama código gerenciado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da8d3a469b957444935150f91567636aef0fb38a
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975258"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Código misto e informações ausentes na janela Pilha de Chamadas
Devido às diferenças entre as pilhas de chamadas para código gerenciado e nativo, o depurador nem sempre pode mostrar a pilha de chamadas completa quando os tipos de código são misturados. Quando o código nativo chama o código gerenciado, você pode observar as seguintes discrepâncias na janela **Pilha de Chamadas**:

- O quadro nativo imediatamente acima do código gerenciado pode estar ausente da janela **Pilha de Chamadas**. Para obter mais informações, consulte [como: sair do código gerenciado quando quadros nativos estão ausentes na janela pilha de chamadas](how-to-use-the-call-stack-window.md).

- Para os aplicativos de modo misto iniciados fora do depurador, a janela **Pilha de Chamadas** pode exibir somente o código gerenciado e nenhum dos quadros nativos estarão visíveis.

  Ambos os casos são razoavelmente incomuns. Na maioria das chamadas nativas para o código gerenciado, as pilhas de chamadas são exibidas corretamente.

## <a name="see-also"></a>Veja também
- [Como usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md)