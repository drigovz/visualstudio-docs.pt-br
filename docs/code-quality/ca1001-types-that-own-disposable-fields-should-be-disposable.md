---
title: 'CA1001: Tipos com campos descartáveis devem ser descartáveis'
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
ms.openlocfilehash: 3bda8fc80992a2246c30e28582eb93b4624ab81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236689"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Tipos com campos descartáveis devem ser descartáveis

|||
|-|-|
|NomeDoTipo|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Categoria|Microsoft.Design|
|Alteração significativa|Não separável – se o tipo não estiver visível fora do assembly.<br /><br /> Quebra-se o tipo é visível fora do assembly.|

## <a name="cause"></a>Causa
Uma classe declara e implementa um campo de instância que é um <xref:System.IDisposable?displayProperty=fullName> tipo e a classe não implementa. <xref:System.IDisposable>

## <a name="rule-description"></a>Descrição da regra
Uma classe implementa a <xref:System.IDisposable> interface para descartar os recursos não gerenciados que ele possui. Um campo de instância que é <xref:System.IDisposable> um tipo indica que o campo possui um recurso não gerenciado. Uma classe que declara que um <xref:System.IDisposable> campo é indiretamente proprietário de um recurso não gerenciado e deve <xref:System.IDisposable> implementar a interface. Se a classe não possui diretamente nenhum recurso não gerenciado, ela não deve implementar um finalizador.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, implemente <xref:System.IDisposable> e, a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> partir do método <xref:System.IDisposable.Dispose%2A> , chame o método do campo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma classe que viola a regra e uma classe que cumpre a regra implementando <xref:System.IDisposable>. A classe não implementa um finalizador porque a classe não possui diretamente nenhum recurso não gerenciado.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2213: os campos descartáveis devem ser descartados](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

[CA2216: Tipos descartáveis devem declarar finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA2215: Os métodos Dispose devem chamar a classe base Dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

[CA1049: Tipos que possuem recursos nativos devem ser descartáveis](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)