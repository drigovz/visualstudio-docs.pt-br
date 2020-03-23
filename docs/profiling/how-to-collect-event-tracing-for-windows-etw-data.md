---
title: Como coletar dados de ETW (Rastreamento de Eventos para Windows) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2fa0547682351d1a7ba4efe4ce3b4350b906462c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779019"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Como coletar dados do ETW (Rastreamento de Eventos para Windows)

O ETW (Rastreamento de Eventos para Windows) é um recurso de rastreamento eficiente em nível de kernel que permite que o criador de perfil registre log de eventos de kernel ou de eventos definidos pelo aplicativo. Os dados coletados pelo provedor de eventos podem ser exibidos somente usando a opção /**Summary:ETW** da ferramenta de linha de comando [VSPerfReport](../profiling/vsperfreport.md). Você pode usar esse relatório para determinar o local em que ocorrem problemas de desempenho no aplicativo.

> [!NOTE]
> Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Para habilitar provedores de rastreamento de eventos

1. No **Performance Explorer**, clique com o botão direito do mouse na sessão de desempenho e, em seguida, clique em **Propriedades**.

2. Nas **Páginas de Propriedades**, clique nas propriedades de **Eventos do Windows**.

3. Na lista **Selecionar provedor de rastreamento de eventos do qual coletar dados**, selecione os provedores de eventos que você deseja usar para analisar seu aplicativo.

## <a name="see-also"></a>Confira também

[Configure sessões de desempenho](../profiling/configuring-performance-sessions.md)
