---
title: A depuração de modo misto para processos IA64 não é compatível. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0668ff847922934f88f98b20c1ac01e6b119e401
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980928"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>A depuração de modo misto para processos IA64 não é compatível.
O Visual Studio não oferece suporte à depuração de modo misto de código gerenciado e nativo em processos IA64. Isso significa que, durante a depuração, você não pode depurar de código gerenciado para código nativo e vice-versa.  
  
### <a name="workarounds"></a>Soluções alternativas  
  
-   Depure seu código gerenciado e nativo em sessões separadas de depuração.  
  
     - ou -  
  
     Depure seu código misto como um processo de 32 bits, como descrito nos procedimentos a seguir.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Para alterar a plataforma para 32 bits (Visual Basic ou C#)  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e clique em **Propriedades** no menu de atalho.  
  
2.  Nas páginas de propriedades, clique na guia **Compilar** ou **Depurar**.  
  
3.  Clique em **Plataforma** e selecione x86 na lista de plataformas.  
  
     Por padrão, os compiladores padrão do Visual Basic e do C# produzem código para ser executado em qualquer CPU. Em um computador de 64 bits, esses binários são executados como processos de 64 bits. Para executar em um processo de 32 bits, você deve escolher **Win32** e não **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Para alterar a plataforma para 32 bits (C/C++)  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e clique em **Propriedades** no menu de atalho.  
  
2.  Nas Páginas de Propriedades, clique em **Plataforma** e selecione Win32 na lista de plataformas.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos de 64 bits](../debugger/debug-64-bit-applications.md)