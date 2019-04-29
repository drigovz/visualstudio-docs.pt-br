---
title: 'CA2121: Construtores estáticos devem ser particulares'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9aecfe8e0be0f5d32df41b7eb164423fd4d405db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62544997"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Construtores estáticos devem ser particulares

|||
|-|-|
|NomeDoTipo|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo tem um construtor estático que não é privado.

## <a name="rule-description"></a>Descrição da regra

Um construtor estático, também conhecido como um construtor de classe é usado para inicializar um tipo. O sistema chama o construtor estático antes que a primeira instância do tipo seja criada ou que outros membros estáticos sejam referenciados. O usuário não tem controle sobre quando o construtor estático é chamado. Se não for privado, um construtor estático poderá ser chamado por um código diferente do sistema. Dependendo das operações realizadas no construtor, isso pode causar um comportamento inesperado.

Essa regra é imposta pelos compiladores c# e Visual Basic.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Violações normalmente são causadas por uma das seguintes ações:

- Definido um construtor estático para o seu tipo e não faz privada.

- O compilador de linguagem de programação adicionado um construtor estático padrão para seu tipo e não faz privada.

Para corrigir o primeiro tipo de violação, faça seu construtor estático privado. Para corrigir o segundo tipo, adicione um construtor estático privado para seu tipo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima essas violações. Se o projeto de software requer uma chamada explícita para um construtor estático, é provável que o design contém falha grave e deve ser revisado.