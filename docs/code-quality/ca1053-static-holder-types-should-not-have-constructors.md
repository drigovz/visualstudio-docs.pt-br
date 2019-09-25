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
ms.openlocfilehash: 44bdb8c12b48a983b88e6a035fc1522856b306be
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235580"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053: Tipos de detentor estáticos não devem ter construtores padrão

|||
|-|-|
|NomeDoTipo|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

> [!NOTE]
> A regra CA1053 é combinada [em CA1052: Os tipos de detentor estáticos](ca1052-static-holder-types-should-be-sealed.md) devem ser lacrados em [analisadores do FxCop](fxcop-analyzers.yml).

## <a name="cause"></a>Causa

Um tipo público público ou aninhado declara somente membros estáticos e tem um construtor padrão.

## <a name="rule-description"></a>Descrição da regra

O construtor padrão é desnecessário porque chamar membros estáticos não requer uma instância do tipo. Além disso, como o tipo não tem membros não estáticos, a criação de uma instância não fornece acesso a nenhum dos membros do tipo.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova o construtor padrão.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. A presença do construtor padrão sugere que o tipo não é um tipo estático.