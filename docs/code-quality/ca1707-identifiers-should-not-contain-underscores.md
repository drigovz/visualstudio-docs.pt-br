---
title: 'CA1707: Identificadores não devem conter sublinhados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252577"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Identificadores não devem conter sublinhados

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Categoria|Microsoft.Naming|
|Alteração significativa|Quebra-quando elevado em assemblies<br /><br /> Não separável-quando elevado em parâmetros de tipo|

## <a name="cause"></a>Causa

O nome de um identificador contém o caractere de sublinhado (\_).

## <a name="rule-description"></a>Descrição da regra

Por convenção, os nomes de identificador não contêm o caractere de sublinhado (\_). A regra verifica namespaces, tipos, membros e parâmetros.

As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Isso reduz a curva de aprendizado necessária para novas bibliotecas de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Remova todos os caracteres de sublinhado do nome.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprimir avisos para código de produção. No entanto, é seguro suprimir esse aviso para o código de teste. Você pode suprimir os avisos dessa regra definindo sua [severidade](use-roslyn-analyzers.md#rule-severity) como **None**. 

## <a name="related-rules"></a>Regras relacionadas

- [CA1709: Os identificadores devem ser totais corretamente @ no__t-0
- [CA1708: Os identificadores devem ser diferentes em mais do que caso @ no__t-0
