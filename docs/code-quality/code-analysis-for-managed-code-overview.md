---
title: Análise de código para código gerenciado
ms.date: 08/27/2020
description: Saiba mais sobre analisadores de código baseados em .NET Compiler Platform no Visual Studio. Entenda por que esses analisadores substituem a análise estática do FxCop de assemblies gerenciados.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 643e8457dbbe838d593a7bad38064537b6cbe57d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348522"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visão geral da análise de código para .NET no Visual Studio

O Visual Studio pode executar a análise de código do código gerenciado de duas maneiras: com a [análise herdada](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), também conhecida como análise estática do FxCop de assemblies gerenciados e com os mais modernos [analisadores de código baseados em .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analisadores de código baseados em .NET Compiler Platform, que analisam seu código ao vivo conforme você digita, substituem a análise de código estático do FxCop herdado, que apenas analisa o código compilado.
