---
title: Caixa de diálogo parar depuração em andamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3beefe16f8883eb64d7d0a2641cabf9eb1f702fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729663"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Caixa de diálogo Parar Depuração em Andamento
Essa caixa de diálogo aparece quando o depurador está tentando interromper uma sessão de depuração, mas parar a sessão deve demorar um pouco. Parar uma sessão de depuração normalmente é muito rápido e essa caixa de diálogo não é exibida. Entretanto, às vezes, leva mais tempo para desanexar de todos os processos que estão sendo depurados. Se parar a sessão levar mais do que alguns segundos (ou se ocorrer um erro de desanexação), essa caixa de diálogo será exibida. Se isso ocorrer com frequência, poderá ser devido a um problema interno e você deverá entrar em contato com o Product Support Services.

 Você pode esperar os processos desanexarem e essa caixa de diálogo desaparecer ou usar o botão **Parar Agora** para forçar a terminação imediata.

 **Parar agora** Clique neste botão para encerrar a sessão de depuração imediatamente. O uso de **Stop agora** será encerrado em vez de desanexar os processos que estão sendo depurados. Se você estiver depurando processos do sistema, encerrar os processos com **Parar Agora** poderá ter efeitos inesperados e indesejados.

## <a name="see-also"></a>Consulte também
- [Segurança do depurador](../debugger/debugger-security.md)
- [Desanexando programas](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))