---
title: Roteamento em VSPackages de comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 954d3f25a425652d8adcb31bd36fab06de0d04d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195084"
---
# <a name="command-routing-in-vspackages"></a>Roteamento de comando em VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um comando é roteado em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] baseado no contexto no qual ele é executado. Ela é roteada do contexto inicial para fora para o contexto global.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Algoritmo de roteamento](../../extensibility/internals/command-routing-algorithm.md)  
 Descreve a ordem de resolução de roteamento de comando.  
  
 [Disponibilidade](../../extensibility/internals/command-availability.md)  
 Discute o roteamento de comando.  
  
 [Comandos e menus que usam assemblies de interoperabilidade](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Discute considerações em comandos de roteamento entre código gerenciado e COM.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Objetos do contexto de seleção](../../extensibility/internals/selection-context-objects.md)  
 Discute o modelo de como você pode determinar o foco de contexto de seleção do usuário em uma janela.  
  
 [Comandos, menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica como criar uma interface do usuário que inclui menus, barras de ferramentas e caixas de combinação de comando.
