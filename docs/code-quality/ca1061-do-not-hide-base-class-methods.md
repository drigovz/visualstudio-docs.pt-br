---
title: 'CA1061: Não ocultar métodos de classe base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eacd20dee0758ff481b259807ba52bb78b26f5d2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235383"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Não ocultar métodos de classe base

|||
|-|-|
|NomeDoTipo|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo derivado declara um método com o mesmo nome e com o mesmo número de parâmetros que um de seus métodos base; um ou mais dos parâmetros é um tipo base do parâmetro correspondente no método base; e quaisquer parâmetros restantes têm tipos que são idênticos aos parâmetros correspondentes no método base.

## <a name="rule-description"></a>Descrição da regra
Um método em um tipo base é ocultado por um método de nome idêntico em um tipo derivado quando a assinatura de parâmetro do método derivado difere somente por tipos que são mais fracamente derivados do que os tipos correspondentes na assinatura de parâmetro do método de base.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova ou renomeie o método ou altere a assinatura do parâmetro para que o método não oculte o método base.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um método que viola a regra.

[!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]