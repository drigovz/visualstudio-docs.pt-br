---
title: Roteamento em VSPackages de comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5749875a440a3122a06b81ae9d721e75ded6202c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641293"
---
# <a name="command-routing-in-vspackages"></a>Roteamento de comando em VSPackages
Um comando é roteado em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] baseado no contexto no qual ele é executado. Ela é roteada do contexto inicial para fora para o contexto global.

## <a name="in-this-section"></a>Nesta seção
- [Algoritmo de roteamento de comando](../../extensibility/internals/command-routing-algorithm.md)

 Descreve a ordem de resolução de roteamento de comando.

- [Disponibilidade do comando](../../extensibility/internals/command-availability.md)

 Discute o roteamento de comando.

- [Comandos e menus que usam assemblies de interoperabilidade](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Discute considerações em comandos de roteamento entre código gerenciado e COM.

## <a name="related-sections"></a>Seções relacionadas
- [Objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md)

 Discute o modelo de como você pode determinar o foco de contexto de seleção do usuário em uma janela.

- [Comandos, menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explica como criar uma interface do usuário que inclui menus, barras de ferramentas e caixas de combinação de comando.