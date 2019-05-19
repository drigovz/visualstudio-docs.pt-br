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
ms.openlocfilehash: 354d1d2fe99fa55bba7f8a00bf3e9f760ff1dbaf
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842181"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Fornecer a mensagem ObsoleteAttribute

|||
|-|-|
|NomeDoTipo|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um tipo ou membro marcado usando um <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo que não tem seu <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propriedade especificada.

Por padrão, essa regra olha apenas para membros e tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

<xref:System.ObsoleteAttribute> é usado para marcar membros e tipos de biblioteca preterido. Os clientes de biblioteca devem evitar o uso de qualquer tipo ou membro que está marcado como obsoleto. Isso ocorre porque ele não poderá ter suporte e eventualmente será removido de versões posteriores da biblioteca. Quando um tipo ou membro marcado usando <xref:System.ObsoleteAttribute> é compilado, o <xref:System.ObsoleteAttribute.Message%2A> propriedade do atributo é exibida. Isso dá ao usuário informações sobre o tipo ou o membro obsoleto. Essas informações geralmente incluem quanto o tipo obsoleto ou membro será compatível com os designers de biblioteca e da substituição de preferência para usar.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, adicione a `message` parâmetro para o <xref:System.ObsoleteAttribute> construtor.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprimir um aviso nessa regra porque o <xref:System.ObsoleteAttribute.Message%2A> propriedade fornece informações essenciais sobre o tipo ou membro obsoleto.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (Design). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um membro obsoleto que tenha declarado corretamente <xref:System.ObsoleteAttribute>.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Consulte também

- <xref:System.ObsoleteAttribute?displayProperty=fullName>