---
title: 'CA1001: tipos que tenham campos descartáveis devem ser descartáveis'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f49624e4e39bb0b3c1a0c1be7f32e797536d30eb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431798"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: tipos que tenham campos descartáveis devem ser descartáveis

|||
|-|-|
|NomeDoTipo|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Categoria|Microsoft. Design|
|Alteração significativa|Não separável – se o tipo não estiver visível fora do assembly.<br /><br /> Quebra-se o tipo é visível fora do assembly.|

## <a name="cause"></a>Causa
Uma classe declara e implementa um campo de instância que é um tipo <xref:System.IDisposable?displayProperty=fullName> e a classe não implementa <xref:System.IDisposable>.

## <a name="rule-description"></a>Descrição da regra
Uma classe implementa a interface <xref:System.IDisposable> para descartar os recursos não gerenciados que ela possui. Um campo de instância que é um tipo <xref:System.IDisposable> indica que o campo possui um recurso não gerenciado. Uma classe que declara um campo <xref:System.IDisposable> indiretamente possui um recurso não gerenciado e deve implementar a interface <xref:System.IDisposable>. Se a classe não possui diretamente nenhum recurso não gerenciado, ela não deve implementar um finalizador.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, implemente <xref:System.IDisposable> e, a partir do método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, chame o método <xref:System.IDisposable.Dispose%2A> do campo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma classe que viola a regra e uma classe que cumpre a regra implementando <xref:System.IDisposable>. A classe não implementa um finalizador porque a classe não possui diretamente nenhum recurso não gerenciado.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2213: os campos descartáveis devem ser descartados](../code-quality/ca2213.md)

[CA2216: os tipos descartáveis devem declarar o finalizador](../code-quality/ca2216.md)

[CA2215: métodos Dispose devem chamar o descarte da classe base](../code-quality/ca2215.md)

[CA1049: tipos que tenham recursos nativos devem ser descartáveis](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
