---
title: 'CA1821: Remover finalizadores vazios'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a93ebea78c9258667d7c6ca10e35d22fc4113f48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233435"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Remover finalizadores vazios

|||
|-|-|
|NomeDoTipo|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Categoria|Microsoft.Performance|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo implementa um finalizador que está vazio, chama apenas o finalizador de tipo base ou chama apenas métodos emitidos condicionalmente.

## <a name="rule-description"></a>Descrição da regra

Sempre que possível, evite finalizadores devidos à sobrecarga de desempenho adicional envolvida na vida útil do objeto de rastreamento. O coletor de lixo executa o finalizador antes de coletar o objeto. Isso significa que pelo menos duas coleções são necessárias para coletar o objeto. Um finalizador vazio incorre nessa sobrecarga adicional sem nenhum benefício.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Remova o finalizador vazio. Se um finalizador for necessário para a depuração, coloque todo o finalizador `#if DEBUG / #endif` em diretivas.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprimir uma mensagem dessa regra.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um finalizador vazio que deve ser removido, um finalizador que deve ser colocado `#if DEBUG / #endif` entre diretivas e um finalizador que usa as `#if DEBUG / #endif` diretivas corretamente.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]
