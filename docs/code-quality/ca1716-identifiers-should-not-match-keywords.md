---
title: 'CA1716: Identificadores não devem corresponder a palavras-chave'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a3f030c9c64d975d93aa2aeee90d37f765a6a63
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234050"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Identificadores não devem corresponder a palavras-chave

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Categoria|Microsoft.Naming|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

O nome de um namespace, tipo ou membro de interface ou virtual corresponde a uma palavra-chave reservada em uma linguagem de programação.

Por padrão, essa regra só examina os namespaces, tipos e membros visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Identificadores para namespaces, tipos e membros de interface e virtuais não devem corresponder a palavras-chave definidas por linguagens que se destinam ao Common Language Runtime. Dependendo do idioma usado e da palavra-chave, os erros e as ambiguidades do compilador podem tornar a biblioteca difícil de usar.

Esta regra verifica as palavras-chave nos seguintes idiomas:

- Visual Basic
- C#
- C++/CLI

A comparação que não diferencia maiúsculas de minúsculas é usada para Visual Basic palavras-chave e a comparação que diferencia maiúsculas de minúsculas é usada para os outros idiomas.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Selecione um nome que não apareça na lista de palavras-chave.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Você pode suprimir um aviso dessa regra se estiver convencido de que o identificador não confunde os usuários da API e que a biblioteca pode ser usada em todos os idiomas disponíveis no .NET.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (nomenclatura). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).