---
title: 'CA2202: não descartar objetos várias vezes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e0be715d8aea84fac53ea2a796e71850b961730c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667400"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: não descartar objetos várias vezes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Uma implementação de método contém caminhos de código que podem causar várias chamadas para <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ou um equivalente de Dispose, como um método Close () em alguns tipos, no mesmo objeto.

## <a name="rule-description"></a>Descrição da Regra
 Um método <xref:System.IDisposable.Dispose%2A> corretamente implementado pode ser chamado várias vezes sem gerar uma exceção. No entanto, isso não é garantido e para evitar a geração de um <xref:System.ObjectDisposedException?displayProperty=fullName> você não deve chamar <xref:System.IDisposable.Dispose%2A> mais de uma vez em um objeto.

## <a name="related-rules"></a>Regras relacionadas
 [CA2000: descartar objetos antes de perder o escopo](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere a implementação para que, independentemente do caminho do código, <xref:System.IDisposable.Dispose%2A> seja chamado apenas uma vez para o objeto.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Mesmo se <xref:System.IDisposable.Dispose%2A> para o objeto for conhecido por ser chamado com segurança várias vezes, a implementação poderá mudar no futuro.

## <a name="example"></a>Exemplo
 As instruções aninhadas `using` (`Using` em Visual Basic) podem causar violações do aviso CA2202. Se o recurso IDisposable da instrução `using` interna aninhada contiver o recurso da instrução `using` externa, o método `Dispose` do recurso aninhado liberará o recurso contido. Quando essa situação ocorre, o método `Dispose` da instrução `using` externa tenta descartar seu recurso por uma segunda vez.

 No exemplo a seguir, um objeto <xref:System.IO.Stream> que é criado em uma instrução using externa é liberado no final da instrução using interna no método Dispose do objeto <xref:System.IO.StreamWriter> que contém o objeto `stream`. No final da instrução `using` externa, o objeto `stream` é liberado uma segunda vez. A segunda versão é uma violação do CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Exemplo
 Para resolver esse problema, use um `try` / bloco de `finally` em vez da instrução de `using` externa. No bloco `finally`, verifique se o recurso `stream` não é nulo.

```
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
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>Consulte também
 [padrão de descarte](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) de <xref:System.IDisposable?displayProperty=fullName>
