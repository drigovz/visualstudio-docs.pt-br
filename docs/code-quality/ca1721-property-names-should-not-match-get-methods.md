---
title: 'CA1721: Nomes de propriedades não devem corresponder a métodos get'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d34af9e8bc814e96976fd451dc64227c730646d2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981955"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Nomes de propriedades não devem corresponder a métodos get

|||
|-|-|
|NomeDoTipo|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um membro público ou protegido começa com 'Get' e, caso contrário, corresponde ao nome de uma propriedade pública ou protegida. Por exemplo, um tipo que contém um método chamado 'GetColor' e uma propriedade chamada 'Color' viola essa regra.

## <a name="rule-description"></a>Descrição da regra
 Os métodos GET e propriedades devem ter nomes que diferenciem claramente a função.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Essa consistência reduz o tempo necessário para conhecer uma nova biblioteca de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Altere o nome para que ele não coincide com o nome de um método que é prefixado com 'Get'.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.

> [!NOTE]
> Esse aviso pode ser excluído se o método Get é causado pela implementação de interface IExtenderProvider.

## <a name="example"></a>Exemplo
 O exemplo a seguir contém um método e propriedade que violam essa regra.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1024: Usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)