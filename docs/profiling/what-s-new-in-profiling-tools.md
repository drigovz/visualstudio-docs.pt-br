---
title: Novidades na criação de perfil do Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 0c05595c311367ca94e3327afd28bc5fa05f7ec2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "57871072"
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Novidades nas ferramentas de criação de perfil do [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

As Ferramentas de Diagnóstico incluem novas visualizações para ajudar você a identificar problemas em seu aplicativo que precisam de correção. As Ferramentas de Diagnóstico agora incluem suporte para aplicativos ASP.NET.

Para saber mais, veja as [Notas de versão para [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](/visualstudio/releasenotes/vs2017-relnotes).

Uma guia **Resumo** foi adicionada às ferramentas para ajudar você a focar áreas-chave da sua análise de desempenho. Essa guia mostra quantos eventos ocorreram, permite que você tire instantâneos do heap e que você habilite rapidamente a coleta de dados de uso da CPU. Essa exibição mostra qualquer evento do [Application Insights](/azure/azure-monitor/app/visual-studio) ou da [Análise da Interface do Usuário](/visualstudio/releasenotes/vs2017-relnotes). Além disso, para o Visual Studio Enterprise, essa exibição também mostra eventos do IntelliTrace.

![Guia Resumo das Ferramentas de Diagnóstico](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

A ferramenta de uso da CPU tem [novas visualizações](../profiling/Beginners-Guide-to-Performance-Profiling.md) para ajudar você a identificar as funções que têm uma probabilidade maior de causar problemas de desempenho. A nova exibição **Chamador/Computador Chamado** permite a investigação dos custos de chamadas de função feitas de/para uma função selecionada.

![Exibição do Chamador/Computador Chamado da Chamada das Ferramentas de Diagnóstico](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Consulte também

- [Perfil no Visual Studio](../profiling/index.md)
- [Introdução às ferramentas de criação de perfil](../profiling/profiling-feature-tour.md)