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
ms.openlocfilehash: 9ef0daf5fd28bd829edcdce412839b03ed8347bf
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745436"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erro: Só há suporte para a depuração de modo misto para processos x64 quando o Microsoft .NET Framework 4 ou superior é usado
Para depurar código nativo e gerenciado misto em um processo de 64 bits, você deve ter o .NET Framework versão 4. Não há suporte para a depuração de modo misto dos processos de 64 bits com as versões do .NET Framework anteriores à 4.

### <a name="to-correct-this-error"></a>Para corrigir este erro

- Execute uma das seguintes etapas:

  - Atualize o .NET Framework versão 4.

  - Crie uma versão de 32 bits do aplicativo para depuração.

## <a name="see-also"></a>Consulte também
- [Depuração remota](../debugger/remote-debugging.md)