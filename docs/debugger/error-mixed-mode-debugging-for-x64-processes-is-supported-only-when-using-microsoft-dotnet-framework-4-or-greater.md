---
title: 'Erro: Modo misto de depuração para processos x64 é suportada somente ao usar o Microsoft .NET Framework 4 ou maior | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 61c92460976ec9b95163b83744ee0b01b6ebc572
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986079"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erro: Só há suporte para a depuração de modo misto para processos x64 quando o Microsoft .NET Framework 4 ou superior é usado
Para depurar código nativo e gerenciado misto em um processo de 64 bits, você deverá ter a versão 4 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. A depuração de modo misto de processos de 64 bits com as versões do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] anteriores à 4 não tem suporte.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Execute uma das seguintes etapas:  
  
  - Atualize seu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para a versão 4.  
  
  - Crie uma versão de 32 bits do aplicativo para depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)