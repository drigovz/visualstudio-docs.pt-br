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
ms.openlocfilehash: 47bbb39cadb6a092f71ebd7b3907f34fcc2782ce
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842044"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Identificadores não devem corresponder a palavras-chave

|||
|-|-|
|NomeDoTipo|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

O nome de um namespace, tipo, ou virtual ou membro de interface corresponde a uma palavra-chave reservada em uma linguagem de programação.

Por padrão, essa regra olha apenas visível externamente namespaces, tipos e membros, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Identificadores de namespaces, tipos e virtuais e os membros de interface não devem corresponder a palavras-chave que são definidas por linguagens que visam o common language runtime. Dependendo da linguagem que é usada e a palavra-chave, ambiguidades e erros do compilador podem dificultar a biblioteca usar.

Esta regra verifica em palavras-chave nos seguintes idiomas:

- Visual Basic
- C#
- C++/CLI

Comparação diferencia maiusculas de minúsculas é usada para palavras-chave do Visual Basic, e a comparação diferencia maiusculas de minúsculas é usada para os outros idiomas.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Selecione um nome que não aparece na lista de palavras-chave.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Se você estiver convencido de que o identificador não confundir os usuários da API, e que a biblioteca é utilizável em todos os idiomas disponíveis no .NET, você pode suprimir um aviso nessa regra.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (nomenclatura). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).