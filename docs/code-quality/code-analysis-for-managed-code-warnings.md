---
title: Avisos da análise de código para código gerenciado
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 566b9827f42f646cd9350cfc015a460485212a09
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90094324"
---
# <a name="net-code-analysis-rules"></a>Regras de análise de código .NET
A análise de código .NET fornece regras que indicam violações de qualidade de código ou sugestões para melhorar a qualidade do código. As regras são organizadas em áreas de regras, como design, localização, desempenho e segurança. Determinadas regras são específicas para o uso da API do .NET, enquanto as regras restantes são sobre a qualidade de código genérica. Esta seção fornece discussões e exemplos detalhados para cada regra.

 A tabela a seguir mostra o tipo de informações que são fornecidas para cada diagnóstico.

|Item|Descrição|
|----------|-----------------|
|Type|O TypeName da regra.|
|RuleId|O identificador exclusivo da regra. RuleId e Category são usados para a supressão na origem de um aviso.|
|Categoria|A categoria do aviso.|
|Alteração significativa|Se a correção de uma violação da regra é uma alteração significativa. Alteração significativa significa que um assembly que tem uma dependência no destino que causou a violação não será recompilado com a nova versão fixa ou pode falhar em tempo de execução devido à alteração. Quando há várias correções disponíveis e pelo menos uma correção é uma alteração significativa e uma correção não é especificada, tanto ' quebra ' quanto ' não separável ' são especificados.|
|Causa|O código gerenciado específico que faz com que a regra gere um aviso.|
|Descrição|Discute os problemas que estão por trás do aviso.|
|Como Corrigir Violações|Explica como alterar o código-fonte para satisfazer a regra e impedir que ela gere um aviso.|
|Quando Suprimir Avisos|Descreve quando é seguro suprimir um aviso da regra.|
|Código de exemplo|Exemplos que violam a regra e exemplos corrigidos que satisfazem a regra.|
|Avisos relacionados|Avisos relacionados.|

## <a name="in-this-section"></a>Nesta seção

|Categoria|Descrição|
|-|-|
|[Regras por ID](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Lista todas as regras por RuleId|
|[Regras de Design](../code-quality/design-warnings.md)|Regras que dão suporte ao design correto da biblioteca, conforme especificado pelas diretrizes de design do .NET.|
|[Regras de documentação](../code-quality/documentation-warnings.md)|Regras que dão suporte ao design de biblioteca bem documentada por meio do uso correto de comentários de documentação XML.|
|[Regras de Globalização](../code-quality/globalization-warnings.md)|Regras que dão suporte a bibliotecas e aplicativos preparados para o mundo.|
|[Regras de Facilidade de Manutenção](../code-quality/maintainability-warnings.md)|Regras que dão suporte à manutenção de biblioteca e aplicativo.|
|[Regras de nomenclatura](../code-quality/naming-warnings.md)|Regras que dão suporte à adesão às convenções de nomenclatura das diretrizes de design do .NET.|
|[Regras de desempenho](../code-quality/performance-warnings.md)|Regras que dão suporte a bibliotecas e aplicativos de alto desempenho.|
|[Regras de portabilidade e interoperabilidade](../code-quality/interoperability-warnings.md)|Regras que dão suporte à portabilidade em diferentes plataformas e interação com clientes COM.|
|[Regras de publicação](../code-quality/publish-warnings.md)|Regras que dão suporte à publicação apropriada de aplicativos .NET.|
|[Regras de confiabilidade](../code-quality/reliability-warnings.md)|Regras que dão suporte à confiabilidade de biblioteca e de aplicativo, como a memória correta e o uso de thread.|
|[Regras de Segurança](../code-quality/security-warnings.md)|Regras que dão suporte a bibliotecas e aplicativos mais seguros.|
|[Regras de uso](../code-quality/usage-warnings.md)|Regras que dão suporte ao uso apropriado do .NET.|
