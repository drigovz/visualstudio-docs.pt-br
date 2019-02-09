---
title: 'CA1725: Nomes de parâmetros devem corresponder à declaração base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54a7926cd0bf8eb2ebf526c1f19a00c71960900c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917682"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Nomes de parâmetros devem corresponder à declaração base

|||
|-|-|
|NomeDoTipo|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um parâmetro em uma substituição do método visível externamente não coincide com o nome do parâmetro em que a declaração do método de base ou o nome do parâmetro na declaração de interface do método.

## <a name="rule-description"></a>Descrição da regra
 A nomenclatura consistente dos parâmetros em uma hierarquia de substituição aumenta a usabilidade das substituições de método. Um nome de parâmetro em um método derivado diferente do nome na declaração de base pode causar confusão em relação à possibilidade do método ser uma substituição do método de base ou de uma nova sobrecarga do método.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, renomeie o parâmetro para corresponder à declaração base. A correção é uma alteração significativa para os métodos visíveis.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra, exceto para os métodos visíveis nas bibliotecas que foram enviados anteriormente.