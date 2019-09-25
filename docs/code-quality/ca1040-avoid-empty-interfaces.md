---
title: 'CA1040: Evitar interfaces vazias'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a316025191ea68b1e63fc849db5b85c8f888a24d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235873"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Evitar interfaces vazias

|||
|-|-|
|NomeDoTipo|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

A interface não declara nenhum membro ou implementa duas ou mais interfaces.

Por padrão, essa regra só examina interfaces visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

As interfaces definem os membros que fornecem um contrato de comportamento ou de uso. A funcionalidade descrita pela interface pode ser adotada por qualquer tipo, independentemente de onde o tipo seja exibido na hierarquia de herança. Um tipo implementa uma interface fornecendo implementações para os membros da interface. Uma interface vazia não define nenhum membro. Portanto, ele não define um contrato que pode ser implementado.

Se o design incluir interfaces vazias que devem ser implementadas pelos tipos, você provavelmente está usando uma interface como um marcador ou uma maneira de identificar um grupo de tipos. Se essa identificação ocorrer em tempo de execução, a maneira correta de fazer isso é usar um atributo personalizado. Use a presença ou a ausência do atributo, ou as propriedades do atributo, para identificar os tipos de destino. Se a identificação deve ocorrer no momento da compilação, é aceitável usar uma interface vazia.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Remova a interface ou adicione membros a ela. Se a interface vazia estiver sendo usada para rotular um conjunto de tipos, substitua a interface por um atributo personalizado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra quando a interface é usada para identificar um conjunto de tipos no momento da compilação.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1040.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma interface vazia.

[!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
[!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
[!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]