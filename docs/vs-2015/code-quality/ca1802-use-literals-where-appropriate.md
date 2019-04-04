---
title: 'CA1802: Usar literais quando apropriado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5990d8ea3720098651d3ed696f6ee5ff907b82f3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922426"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Usar literais quando apropriado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um campo é declarado `static` e `readonly` (`Shared` e `ReadOnly` em [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) e é inicializada com um valor computável no tempo de compilação.

## <a name="rule-description"></a>Descrição da Regra
 O valor de um `static``readonly` campo é calculado em tempo de execução quando o construtor estático para o tipo declarativo é chamado. Se o `static``readonly` campo é inicializado quando ela é declarada e um construtor estático não é declarado explicitamente, o compilador emite um construtor estático para inicializar o campo.

 O valor de uma `const` campo é calculado em tempo de compilação e armazenado nos metadados, o que aumenta o desempenho de tempo de execução quando ele é comparado com um `static``readonly` campo.

 Como o valor atribuído ao campo de destino é computável no tempo de compilação, altere a declaração para um `const` campo para que o valor é calculado em tempo de compilação em vez de em tempo de execução.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, substitua os `static` e `readonly` modificadores com o `const` modificador.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, ou desabilitar a regra, se o desempenho não for uma preocupação.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `UseReadOnly`, que viola a regra e um tipo, `UseConstant`, que satisfaz a regra.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
