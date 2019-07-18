---
title: 'CA2202: Não descartar objetos várias vezes'
ms.date: 07/16/2019
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fb70baa17bee484dc3c31d7c6ce9b302019403
ms.sourcegitcommit: 2bbcba305fd0f8800fd3d9aa16f7647ee27f3a4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300595"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Não descartar objetos várias vezes

|||
|-|-|
|NomeDoTipo|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa

Uma implementação de método contém caminhos de código que podem causar várias <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chamadas para ou um equivalente Dispose, como um método Close () em alguns tipos, no mesmo objeto.

## <a name="rule-description"></a>Descrição da regra

Um método implementado <xref:System.IDisposable.Dispose%2A> corretamente pode ser chamado várias vezes sem gerar uma exceção. No entanto, isso não é garantido e para evitar <xref:System.ObjectDisposedException?displayProperty=fullName> a geração de um <xref:System.IDisposable.Dispose%2A> , você não deve chamar mais de uma vez em um objeto.

## <a name="related-rules"></a>Regras relacionadas

- [CA2000: Descartar objetos antes de perder o escopo](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, altere a implementação para que, independentemente do caminho do código, <xref:System.IDisposable.Dispose%2A> seja chamado apenas uma vez para o objeto.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Mesmo se <xref:System.IDisposable.Dispose%2A> for conhecido que o objeto seja chamado com segurança várias vezes, a implementação poderá ser alterada no futuro.

## <a name="example"></a>Exemplo

As `using` instruções aninhadas (`Using` em Visual Basic) podem causar violações do aviso CA2202. Se o recurso IDisposable da instrução interna `using` aninhada contiver o recurso da instrução externa `using` , o `Dispose` método do recurso aninhado liberará o recurso contido. Quando essa situação ocorre, o `Dispose` método da instrução externa `using` tenta descartar seu recurso por uma segunda vez.

No exemplo a seguir, um <xref:System.IO.Stream> objeto que é criado em uma instrução using externa é liberado no final da instrução using interna no método Dispose <xref:System.IO.StreamWriter> do objeto que contém o `stream` objeto. No final da instrução externa `using` , o `stream` objeto é liberado uma segunda vez. A segunda versão é uma violação do CA2202.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Exemplo

Para resolver esse problema, use um `try` / `finally` bloco em vez da instrução `using` externa. No bloco, verifique se o `stream` recurso não é nulo. `finally`

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    stream?.Dispose();
}
```

> [!TIP]
> A `?.` sintaxe acima é o [operador NULL-Conditional](/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-).

## <a name="see-also"></a>Consulte também

- <xref:System.IDisposable?displayProperty=fullName>
- [Padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern)