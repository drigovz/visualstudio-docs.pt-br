---
title: 'CA1059: Membros não devem expor determinados tipos concretos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97ee4e11ceb3380c204d00203b9e81397a39e362
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235470"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Membros não devem expor determinados tipos concretos

|||
|-|-|
|NomeDoTipo|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um membro visível externamente é um determinado tipo concreto ou expõe determinados tipos concretos por meio de um de seus parâmetros ou valor de retorno. Atualmente, essa regra relata a exposição dos seguintes tipos concretos:

- Um tipo derivado de <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da regra
Um tipo concreto é um tipo que tem uma implementação completa e, por isso, uma instância pode ser criada. Para permitir o uso generalizado do membro, substitua o tipo concreto pela interface sugerida. Isso permite que o membro aceite qualquer tipo que implemente a interface ou seja usado onde um tipo que implementa a interface é esperado.

A tabela a seguir lista os tipos concretos direcionados e suas substituições sugeridas.

|Tipo concreto|Substituição|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> O uso da interface dissocia o membro de uma implementação específica de uma fonte de dados XML.|

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere o tipo concreto para a interface sugerida.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir uma mensagem dessa regra se a funcionalidade específica fornecida pelo tipo concreto for necessária.

## <a name="related-rules"></a>Regras relacionadas
[CA1011: Considere passar tipos base como parâmetros](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)