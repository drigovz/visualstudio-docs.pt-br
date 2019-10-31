---
title: Depuração COM e ActiveX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- COM, debugging
- debugging ActiveX applications
- debugging [Visual Studio], COM
- debugging COM containers
- ActiveX controls, debugging
ms.assetid: 3260b2a7-3239-493d-9271-aedf705c13c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a818cfde2996b26bd9d5f31b128e41f2a9fe2e1
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188688"
---
# <a name="com-and-activex-debugging"></a>Depuração de COM e ActiveX
Essa seção fornece dicas sobre depuração de aplicativos COM e controles ActiveX.

## <a name="in-this-section"></a>Nesta seção
 [Depuração de contêiner e servidor com](../debugger/com-server-and-container-debugging.md) Menciona considerações especiais ao depurar aplicativos COM. Os problemas incluem: depurar um servidor e um contêiner COM usando dois projetos dentro da mesma solução, rastreamento em chamadas que atravessam os limites do processo, definição de pontos de interrupção em funções de retorno de chamada e passagem pelos contêineres e servidores.

 [Como depurar um controle ActiveX](../debugger/how-to-debug-an-activex-control.md) Contém informações sobre a depuração de controles ActiveX. Isso inclui: especificar um contêiner para que a sessão de depuração veja como o código no controle ActiveX é executado, depurar um controle ActiveX associado a dados, simular um contêiner específico e entrar no código do contêiner.

 [Ferramentas de depuração com](../debugger/com-debugging-tools.md) Lista visualizadores e aplicativos de exemplo que podem ser úteis para depurar seu aplicativo COM.

## <a name="related-sections"></a>Seções relacionadas
 [Primeira olhada no depurador](../debugger/debugger-feature-tour.md) Fornece links para as seções maiores da documentação de depuração. As informações incluem: o que há de novo no depurador, configurações e preparação, pontos de interrupção, tratamento de exceções, editar e continuar, depurar C++ código gerenciado, depurar projetos, depurar com e ActiveX, depurar DLLs, depurar SQL e o usuário referências de interface.

## <a name="see-also"></a>Consulte também

- [Segurança do depurador](../debugger/debugger-security.md)
- [Introdução a COM](/cpp/atl/introduction-to-com)
- [Controles ActiveX](/cpp/mfc/activex-controls)
- [Aplicativos de servidor SDI](com-server-and-container-debugging.md)