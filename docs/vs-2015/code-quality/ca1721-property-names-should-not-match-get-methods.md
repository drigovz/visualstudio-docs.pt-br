---
title: 'CA1721: Nomes de propriedade não devem corresponder a métodos get | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 94d120a7656fc9270543ceeb57063124764c4bca
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431195"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Nomes de propriedades não devem corresponder a métodos get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um membro público ou protegido começa com 'Get' e, caso contrário, corresponde ao nome de uma propriedade pública ou protegida. Por exemplo, um tipo que contém um método chamado 'GetColor' e uma propriedade chamada 'Color' viola essa regra.

## <a name="rule-description"></a>Descrição da Regra
 Os métodos GET e propriedades devem ter nomes que diferenciem claramente a função.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz o tempo que é necessário para conhecer uma nova biblioteca de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Altere o nome para que ele não coincide com o nome de um método que é prefixado com 'Get'.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

> [!NOTE]
> Esse aviso pode ser excluído se o método Get é causado pela implementação de interface IExtenderProvider.

## <a name="example"></a>Exemplo
 O exemplo a seguir contém um método e propriedade que violam essa regra.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1024: Usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)
