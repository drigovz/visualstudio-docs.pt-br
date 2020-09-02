---
title: Análise de código para código gerenciado
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d13a8afdfcbeb6ae9f91e39779af8b82b2461000
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89091390"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visão geral da análise de código para .NET no Visual Studio

O Visual Studio pode executar a análise de código do código gerenciado de duas maneiras: com a [análise herdada](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), também conhecida como análise estática do FxCop de assemblies gerenciados e com os mais modernos [analisadores de código baseados em .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analisadores de código baseados em .NET Compiler Platform, que analisam seu código ao vivo conforme você digita, substituem a análise de código estático do FxCop herdado, que apenas analisa o código compilado.
