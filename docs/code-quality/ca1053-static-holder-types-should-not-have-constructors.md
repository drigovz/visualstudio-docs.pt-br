---
title: 'CA1053: Tipos de suporte estático não devem ter construtores'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da5edc8f31510fa01d2132735ede502ad7f6ad6a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922596"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Tipos de suporte estático não devem ter construtores

|||
|-|-|
|NomeDoTipo|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou público aninhado declara apenas membros estáticos e tem um construtor padrão público ou protegido.

## <a name="rule-description"></a>Descrição da regra
 O construtor é desnecessário porque chamar membros estáticos não exige uma instância do tipo. Além disso, porque o tipo não tem membros não estáticos, criando uma instância não fornece acesso a qualquer um dos membros do tipo.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, remova o construtor padrão ou torná-la particular.

> [!NOTE]
>  Alguns compiladores criar automaticamente um construtor padrão público se o tipo de não definir nenhum construtor. Se esse for o caso com seu tipo, adicione um construtor padrão particular para eliminar a violação.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra. A presença do construtor sugere que o tipo não é um tipo estático.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola essa regra. Observe que não há nenhum construtor padrão no código-fonte. Quando esse código é compilado em um assembly, o compilador C# irá inserir um construtor padrão, que irá violar essa regra. Para corrigir isso, declare um construtor particular.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]