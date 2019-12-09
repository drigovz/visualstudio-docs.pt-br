---
title: 'Erro: há suporte para a depuração de modo misto para processos x64 somente ao usar o Microsoft .NET Framework 4 ou superior | Microsoft Docs'
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
ms.openlocfilehash: 67b9d1c737e4490195b209abca824b2d6d51176c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737597"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erro: depuração de modo misto para processos x64 só é suportada durante o uso do Microsoft .NET Framework 4 ou superior
Para depurar código nativo e gerenciado Misto em um processo de 64 bits, você deve ter .NET Framework versão 4. Não há suporte para a depuração de modo misto de processos de 64 bits com versões .NET Framework anteriores a 4.

### <a name="to-correct-this-error"></a>Para corrigir este erro

- Execute uma das seguintes etapas:

  - Atualize seu .NET Framework para a versão 4.

  - Crie uma versão de 32 bits do aplicativo para depuração.

## <a name="see-also"></a>Consulte também
- [Depuração remota](../debugger/remote-debugging.md)