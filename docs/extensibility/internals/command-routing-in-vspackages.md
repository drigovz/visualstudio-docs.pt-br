---
title: Roteamento em VSPackages de comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a534a015f57a738ca65895002a6fec4454f0ae97
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342220"
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