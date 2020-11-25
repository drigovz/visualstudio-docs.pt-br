---
title: Migrar de analisadores do FxCop para analisadores do .NET
ms.custom: SEO-VS-2020
description: Saiba como migrar de analisadores do FxCop para analisadores do .NET
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112209"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migrar de analisadores do FxCop para analisadores do .NET

Análise de origem por .NET Compiler Platform ("Roslyn") analisadores substitui a [análise herdada](code-analysis-for-managed-code-overview.md) para código gerenciado. Muitas das regras de análise herdada (FxCop) já foram reescritas como analisadores de origem.

Antes do Visual Studio 2019 16,8 e do .NET 5,0, esses analisadores foram fornecidos como `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacote NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

A partir do Visual Studio 2019 16,8 e do .NET 5,0, esses analisadores estão [incluídos no SDK do .net](/dotnet/fundamentals/code-analysis/overview). Eles também estão disponíveis como `Microsoft.CodeAnalysis.NetAnalyzers` [pacote NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). `Microsoft.CodeAnalysis.FxCopAnalyzers` Em breve, o pacote NuGet será preterido.

## <a name="migration-steps"></a>Etapas da migração

Siga as etapas abaixo para migrar seu projeto ou solução do `Microsoft.CodeAnalysis.FxCopAnalyzers` para os analisadores do .net:

1. Desinstalar o `Microsoft.CodeAnalysis.FxCopAnalyzers` pacote NuGet

2. [Habilitar ou instalar analisadores .NET](install-net-analyzers.md)

3. Habilitar regras adicionais: `Microsoft.CodeAnalysis.NetAnalyzers` é muito mais conservador em comparação com `Microsoft.CodeAnalysis.FxCopAnalyzers` . Ao contrário do pacote FxCopAnalyzers, ele tem apenas algumas regras de correção que são [habilitadas por padrão como avisos de compilação](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Você pode [habilitar regras adicionais](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) Personalizando a propriedade do MSBuild do [analysismode](/dotnet/core/project-sdk/msbuild-props#analysismode) . Por exemplo, definir a propriedade como `AllEnabledByDefault` habilitará todas as regras de autoridade de certificação aplicáveis como avisos de compilação por padrão.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Confira também

- [Análise de código-fonte versus análise herdada](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Migrar da análise herdada para os analisadores do .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Habilitar ou instalar analisadores .NET](install-net-analyzers.md)
- [Perguntas frequentes sobre os analisadores do .NET](net-analyzers-faq.md)
- [Configurar analisadores .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
