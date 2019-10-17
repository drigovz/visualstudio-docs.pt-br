---
title: 'CA1062: validar argumentos de métodos públicos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6019956d37d420b72275223148c2a3468a820884
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440714"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: validar argumentos de métodos públicos

|||
|-|-|
|NomeDoTipo|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Categoria|Microsoft. Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um método visível externamente faz referência a um de seus argumentos de referência sem verificar se esse argumento é `null` (`Nothing` em Visual Basic).

## <a name="rule-description"></a>Descrição da regra

Todos os argumentos de referência que são passados para métodos externos visíveis devem ser verificados em relação a `null`. Se apropriado, lança um <xref:System.ArgumentNullException> quando o argumento é `null`.

Se um método puder ser chamado de um assembly desconhecido porque é declarado público ou protegido, você deve validar todos os parâmetros do método. Se o método for projetado para ser chamado somente por assemblies conhecidos, você deverá tornar o método interno e aplicar o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ao assembly que contém o método.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, valide cada argumento de referência em relação a `null`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Você pode suprimir um aviso dessa regra se tiver certeza de que o parâmetro de referência foi validado por outra chamada de método na função.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um método que viola a regra e um método que satisfaz a regra.

```csharp
using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException(nameof(input));
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException(NameOf(input))
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Exemplo

Os construtores de cópia que populam campos ou propriedades que são objetos de referência também podem violar a regra CA1062. A violação ocorre porque o objeto copiado que é passado para o construtor de cópia pode ser `null` (`Nothing` em Visual Basic). Para resolver a violação, use um método estático (compartilhado no Visual Basic) para verificar se o objeto copiado não é nulo.

No exemplo de classe `Person` a seguir, o objeto `other` que é passado para o construtor de cópia `Person` pode ser `null`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Exemplo

No exemplo a seguir revisado `Person`, o objeto `other` que é passado para o construtor de cópia é verificado primeiro para nulo no método `PassThroughNonNull`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException(nameof(person));
        return person;
    }
}
```
