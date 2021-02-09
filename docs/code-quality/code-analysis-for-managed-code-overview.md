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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 542747f650888b384a9f9c4910b0d9caea93e948
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860562"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visão geral da análise de código para .NET no Visual Studio

O Visual Studio pode executar a análise de código do código gerenciado de duas maneiras: com a [análise herdada](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), também conhecida como análise estática do FxCop de assemblies gerenciados e com os mais modernos [analisadores de código baseados em .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analisadores de código baseados em .NET Compiler Platform, que analisam seu código ao vivo conforme você digita, substituem a análise de código estático do FxCop herdado, que apenas analisa o código compilado.
