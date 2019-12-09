---
title: 'CA1041: forneça a mensagem ObsoleteAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dd1799f67036ab55de5b136d746ce938835de87f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668321"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: fornecer mensagem ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Categoria|Microsoft. Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo ou membro é marcado usando um atributo <xref:System.ObsoleteAttribute?displayProperty=fullName> que não tem sua propriedade <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> especificada.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.ObsoleteAttribute> é usado para marcar Membros e tipos de biblioteca preteridos. Os consumidores de biblioteca devem evitar o uso de qualquer tipo ou membro marcado como obsoleto. Isso ocorre porque ele pode não ter suporte e, eventualmente, será removido das versões posteriores da biblioteca. Quando um tipo ou membro marcado usando <xref:System.ObsoleteAttribute> é compilado, a propriedade <xref:System.ObsoleteAttribute.Message%2A> do atributo é exibida. Isso dá ao usuário informações sobre o tipo ou o membro obsoleto. Essas informações geralmente incluem quanto tempo o tipo ou membro obsoleto será compatível com os designers de biblioteca e a substituição preferida a ser usada.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione o parâmetro `message` ao Construtor <xref:System.ObsoleteAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir um aviso dessa regra porque a propriedade <xref:System.ObsoleteAttribute.Message%2A> fornece informações críticas sobre o tipo ou o membro obsoleto.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um membro obsoleto que tem um <xref:System.ObsoleteAttribute> declarado corretamente.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Consulte também
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
