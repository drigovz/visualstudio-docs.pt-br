---
title: Misto de código e informações ausentes na janela pilha de chamadas | Microsoft Docs
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
ms.openlocfilehash: dc43ba24e821c00adb4efb64e4785e02dae31f28
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992549"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Código misto e informações ausentes na janela Pilha de Chamadas
Devido às diferenças entre as pilhas de chamadas para código gerenciado e nativo, o depurador nem sempre pode mostrar a pilha de chamadas completa quando os tipos de código são misturados. Quando o código nativo chama o código gerenciado, você pode observar as seguintes discrepâncias na janela **Pilha de Chamadas**:  
  
- O quadro nativo imediatamente acima do código gerenciado pode estar ausente da janela **Pilha de Chamadas**. Para obter mais informações, confira [Como: Sair do código gerenciado quando quadros nativos estiverem ausentes na janela Pilha de Chamadas](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- Para os aplicativos de modo misto iniciados fora do depurador, a janela **Pilha de Chamadas** pode exibir somente o código gerenciado e nenhum dos quadros nativos estarão visíveis.  
  
  Ambos os casos são razoavelmente incomuns. Na maioria das chamadas nativas para o código gerenciado, as pilhas de chamadas são exibidas corretamente.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Usar a janela de pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md)