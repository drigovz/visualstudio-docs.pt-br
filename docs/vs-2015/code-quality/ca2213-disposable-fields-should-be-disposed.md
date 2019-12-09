---
title: 'CA2213: campos descartáveis devem ser descartados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662895"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: os campos descartáveis devem ser descartados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> declara campos que são de tipos que também implementam <xref:System.IDisposable>. O método <xref:System.IDisposable.Dispose%2A> do campo não é chamado pelo método <xref:System.IDisposable.Dispose%2A> do tipo declarativo.

## <a name="rule-description"></a>Descrição da Regra
 Um tipo é responsável por descartar todos os seus recursos não gerenciados; Isso é feito com a implementação de <xref:System.IDisposable>. Essa regra verifica se um tipo descartável `T` declara um campo `F` que é uma instância de um tipo descartável `FT`. Para cada campo `F`, a regra tenta localizar uma chamada para `FT.Dispose`. A regra pesquisa os métodos chamados por `T.Dispose` e um nível inferior (os métodos chamados pelos métodos chamados por `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, chame <xref:System.IDisposable.Dispose%2A> em campos que são de tipos que implementam <xref:System.IDisposable> se você for responsável por alocar e liberar os recursos não gerenciados mantidos pelo campo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se você não for responsável por liberar o recurso mantido pelo campo ou se a chamada para <xref:System.IDisposable.Dispose%2A> ocorrer em um nível de chamada mais profundo do que as verificações de regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um `TypeA` de tipo que implementa <xref:System.IDisposable> (`FT` na discussão anterior).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um `TypeB` de tipo que viola essa regra declarando um campo `aFieldOfADisposableType` (`F` na discussão anterior) como um tipo descartável (`TypeA`) e não chamando <xref:System.IDisposable.Dispose%2A> no campo. `TypeB` corresponde a `T` na discussão anterior.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Consulte também
 [padrão de descarte](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) de <xref:System.IDisposable?displayProperty=fullName>
