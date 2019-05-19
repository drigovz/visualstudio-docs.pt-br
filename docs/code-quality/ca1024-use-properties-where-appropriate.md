---
title: 'CA1024: Usar propriedades quando apropriado'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bfedb55c0dcdb1077faea03bca56488ab3da1525
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842464"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Usar propriedades quando apropriado

|||
|-|-|
|NomeDoTipo|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um método tem um nome que começa com `Get`, não usa nenhum parâmetro e retorna um valor que não é uma matriz.

Por padrão, essa regra olha apenas métodos públicos e protegidos, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Na maioria dos casos, as propriedades representam dados e os métodos executam ações. As propriedades são acessadas como campos, o que os torna mais fácil de usar. Um método é um bom candidato para se tornar uma propriedade, se houver uma das seguintes condições:

- Não usa nenhum argumento e retorna as informações de estado de um objeto.

- Aceita um único argumento para definir alguma parte do estado de um objeto.

Propriedades devem se comportar como se fossem campos; Se o método não for possível, ele não deve ser alterado para uma propriedade. Métodos são melhores do que as propriedades nas seguintes situações:

- O método executa uma operação demorada. O método é perceivably mais lento do que o tempo necessário para definir ou obter o valor de um campo.

- O método executa uma conversão. Acesso a um campo não retorna uma versão convertida dos dados que ele armazena.

- O método Get tem um efeito colateral observável. Recuperando o valor de um campo não produz nenhum efeito colateral.

- A ordem de execução é importante. Definindo o valor de um campo não se baseia na ocorrência de outras operações.

- Chamar o método duas vezes em sucessão gera resultados diferentes.

- O método é estático, mas retorna um objeto que pode ser alterado pelo chamador. Recuperando o valor de um campo não permite que o chamador alterar os dados armazenados pelo campo.

- O método retorna uma matriz.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, altere o método a uma propriedade.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprima um aviso nessa regra, se o método de atender a pelo menos um dos critérios listados anteriormente.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1024.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (Design). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="control-property-expansion-in-the-debugger"></a>Expansão de propriedade de controle no depurador

Um motivo que os programadores evitar o uso de uma propriedade é porque eles não deseja que o depurador autoexpandi-lo. Por exemplo, a propriedade pode envolver a alocação de um objeto grande ou chamar um P/Invoke, mas ele realmente não pode ter nenhum efeito colateral observável.

Você pode impedir que o depurador de propriedades autoexpanding aplicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. O exemplo a seguir mostra esse atributo está sendo aplicado a uma propriedade de instância.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp
using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]
            }
        }
    }
}
```

## <a name="example"></a>Exemplo

O exemplo a seguir contém vários métodos que devem ser convertidas em propriedades e vários que devem não porque eles não se comportam como campos.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]