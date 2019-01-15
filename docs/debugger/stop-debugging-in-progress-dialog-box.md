---
title: Parar a depuração na caixa de diálogo de progresso | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3abce02ba1804ff619a7d0f24da35747c2f9ff91
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883127"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Caixa de diálogo Parar Depuração em Andamento
Essa caixa de diálogo aparece quando o depurador está tentando interromper uma sessão de depuração, mas parar a sessão deve demorar um pouco. Parar uma sessão de depuração normalmente é muito rápido e essa caixa de diálogo não é exibida. Entretanto, às vezes, leva mais tempo para desanexar de todos os processos que estão sendo depurados. Se parar a sessão levar mais do que alguns segundos (ou se ocorrer um erro de desanexação), essa caixa de diálogo será exibida. Se isso ocorrer com frequência, poderá ser devido a um problema interno e você deverá entrar em contato com o Product Support Services.  
  
 Você pode esperar os processos desanexarem e essa caixa de diálogo desaparecer ou usar o botão **Parar Agora** para forçar a terminação imediata.  
  
 **Parar Agora**  
 Clique neste botão para encerrar imediatamente a sessão de depuração. Usando o **parar agora** encerrará em vez de desanexar os processos que estão sendo depurados. Se você estiver depurando processos do sistema, encerrar os processos com **Parar Agora** poderá ter efeitos inesperados e indesejados.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Desanexação de programas](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))