---
title: 'CA1821: Remova finalizadores vazios | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5a6175871e74bf3cb99610dce0926f0982f331d4
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58923289"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Remover finalizadores vazios
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um tipo implementa um finalizador que está vazia, chama apenas o finalizador do tipo base ou chama somente emitidos condicionalmente métodos.

## <a name="rule-description"></a>Descrição da Regra
 Sempre que possível, evite finalizadores por conta da sobrecarga adicional no desempenho envolvida no acompanhamento do tempo de vida do objeto. O coletor de lixo executará o finalizador antes que ele coleta o objeto. Isso significa que as duas coleções será necessárias para coletar o objeto. Um finalizador vazio incorre essa sobrecarga agregada sem nenhum benefício.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remova o finalizador vazio. Se um finalizador é necessário para a depuração, coloque o finalizador todo `#if DEBUG / #endif` diretivas.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima uma mensagem a partir dessa regra. Falha ao suprimir a finalização reduz o desempenho e não oferece nenhum benefício.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um finalizador vazio que deve ser removido, um finalizador que deve ser colocado entre `#if DEBUG / #endif` diretivas e um finalizador que usa o `#if DEBUG / #endif` diretivas corretamente.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
