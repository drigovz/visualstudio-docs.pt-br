---
title: 'Erro: Modo misto de depuração para processos x64 é suportada somente ao usar o Microsoft .NET Framework 4 ou maior | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d338ee3660c4459510de7b01b42cb3670328e4c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923520"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erro: Só há suporte para a depuração de modo misto para processos x64 quando o Microsoft .NET Framework 4 ou superior é usado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para depurar código nativo e gerenciado misto em um processo de 64 bits, você deverá ter a versão 4 do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. A depuração de modo misto de processos de 64 bits com as versões do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] anteriores à 4 não tem suporte.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Execute uma das seguintes etapas:  
  
    -   Atualize seu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] para a versão 4.  
  
    -   Crie uma versão de 32 bits do aplicativo para depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Configurar as ferramentas remotas no dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
