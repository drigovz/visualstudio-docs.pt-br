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
ms.openlocfilehash: 1423cbcfcae53948f7b9c9cd52eb90f57251bc24
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851061"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erro: Só há suporte para a depuração de modo misto para processos x64 quando o Microsoft .NET Framework 4 ou superior é usado
Para depurar código nativo e gerenciado misto em um processo de 64 bits, você deverá ter a versão 4 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. A depuração de modo misto de processos de 64 bits com as versões do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] anteriores à 4 não tem suporte.

### <a name="to-correct-this-error"></a>Para corrigir este erro

- Execute uma das seguintes etapas:

  - Atualize seu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para a versão 4.

  - Crie uma versão de 32 bits do aplicativo para depuração.

## <a name="see-also"></a>Consulte também
- [Depuração remota](../debugger/remote-debugging.md)