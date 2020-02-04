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
ms.openlocfilehash: f4e5aad0ffcd6febce411d952b1b36a0669b109a
ms.sourcegitcommit: bb72ce6ec173f3ae06c7ae57322c43690f27553c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2020
ms.locfileid: "76967304"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Visão geral da análise de código para código gerenciado no Visual Studio

O Visual Studio pode executar a análise de código do código gerenciado de duas maneiras: com a [análise herdada](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), também conhecida como análise estática do FxCop de assemblies gerenciados e com os mais modernos [analisadores de código baseados em .net Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analisadores de código baseados em .NET Compiler Platform, que analisam seu código ao vivo conforme você digita, substituem a análise de código estático do FxCop herdado, que apenas analisa o código compilado.

