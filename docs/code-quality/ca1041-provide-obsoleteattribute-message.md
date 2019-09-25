---
title: 'CA1041: Fornecer a mensagem ObsoleteAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6620ac646c7fe20de856185708effc9e1a331e57
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235862"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Fornecer a mensagem ObsoleteAttribute

|||
|-|-|
|NomeDoTipo|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Categoria|Microsoft.Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo ou membro é marcado usando um <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo que não tem sua <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propriedade especificada.

Por padrão, essa regra só examina os membros e tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

<xref:System.ObsoleteAttribute>é usado para marcar Membros e tipos de biblioteca preteridos. Os consumidores de biblioteca devem evitar o uso de qualquer tipo ou membro marcado como obsoleto. Isso ocorre porque ele pode não ter suporte e, eventualmente, será removido das versões posteriores da biblioteca. Quando um tipo ou membro marcado usando <xref:System.ObsoleteAttribute> é compilado, a <xref:System.ObsoleteAttribute.Message%2A> Propriedade do atributo é exibida. Isso dá ao usuário informações sobre o tipo ou o membro obsoleto. Essas informações geralmente incluem quanto tempo o tipo ou membro obsoleto será compatível com os designers de biblioteca e a substituição preferida a ser usada.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, adicione o `message` parâmetro <xref:System.ObsoleteAttribute> ao construtor.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprimir um aviso dessa regra porque a <xref:System.ObsoleteAttribute.Message%2A> propriedade fornece informações críticas sobre o tipo ou o membro obsoleto.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um membro obsoleto que tem um declarado <xref:System.ObsoleteAttribute>corretamente.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Consulte também

- <xref:System.ObsoleteAttribute?displayProperty=fullName>