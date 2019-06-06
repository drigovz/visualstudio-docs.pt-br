---
title: 'CA1030: Usar eventos quando apropriado'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9a3d2ef30018c7fe57f1e7d728ba1dd152f56f5
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714286"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Usar eventos quando apropriado

|||
|-|-|
|NomeDoTipo|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um nome de método começa com um dos seguintes:

- AddOn
- RemoveOn
- Fogo
- Gerar

Por padrão, essa regra olha apenas para métodos externamente visíveis, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Essa regra detecta métodos que têm nomes que seriam usados normalmente em eventos. Os eventos seguem o padrão de design do observador ou publicar-assinar; eles são usados quando uma alteração de estado em um objeto deve ser comunicada aos outros objetos. Se um método é chamado em resposta a uma alteração de estado claramente definida, o método deve ser invocado por um manipulador de eventos. Os objetos que chamam o método devem acionar eventos, em vez de chamar o método diretamente.

Alguns exemplos comuns de eventos são encontrados em aplicativos de interface do usuário em que uma ação do usuário, como clicar em um botão faz com que um segmento de código a ser executado. O modelo de evento do .NET não está limitado a interfaces do usuário. Ele deve ser usado em qualquer lugar, que você deve comunicar o estado muda para um ou mais objetos.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Se o método é chamado quando o estado de um objeto é alterado, considere alterar o design para usar o modelo de evento do .NET.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprima um aviso nessa regra, se o método não funciona com o modelo de evento do .NET.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1030.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (Design). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).
