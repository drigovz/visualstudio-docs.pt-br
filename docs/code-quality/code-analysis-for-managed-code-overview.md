---
title: Análise de código para código gerenciado
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 901c66a97a763345ee32b1a1540a7998934d0ff3
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248978"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Visão geral da análise de código para código gerenciado no Visual Studio

O Visual Studio pode executar a análise de código do código gerenciado de duas maneiras: com a [análise herdada](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), também conhecida como análise estática do FxCop de assemblies gerenciados e com os mais modernos [analisadores de código baseados em .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analisadores de código baseados em .NET Compiler Platform, que analisam seu código ao vivo conforme você digita, substituem a análise de código estático do FxCop herdado, que apenas analisa o código compilado.
