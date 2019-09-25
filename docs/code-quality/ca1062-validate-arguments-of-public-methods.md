---
title: 'CA1062: Validar argumentos de métodos públicos'
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
ms.openlocfilehash: 8106a4c0244cbd79e88a2bdc50e04ea74627dab4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235331"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Validar argumentos de métodos públicos

|||
|-|-|
|NomeDoTipo|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Categoria|Microsoft.Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um método visível externamente faz referência a um de seus argumentos de referência sem verificar se esse argumento é `null` (`Nothing` em Visual Basic).

## <a name="rule-description"></a>Descrição da regra

Todos os argumentos de referência que são passados para métodos externos visíveis devem ser verificados em relação `null`a. Se apropriado, acione um <xref:System.ArgumentNullException> quando o argumento for `null`.

Se um método puder ser chamado de um assembly desconhecido porque é declarado público ou protegido, você deve validar todos os parâmetros do método. Se o método for projetado para ser chamado somente por assemblies conhecidos, você deverá tornar o método interno e aplicar o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo ao assembly que contém o método.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, valide cada argumento de referência em `null`relação a.

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
                throw new ArgumentNullException("input");
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
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Exemplo

Os construtores de cópia que populam campos ou propriedades que são objetos de referência também podem violar a regra CA1062. A violação ocorre porque o objeto copiado que é passado para o construtor de cópia `null` pode`Nothing` ser (em Visual Basic). Para resolver a violação, use um método estático (compartilhado no Visual Basic) para verificar se o objeto copiado não é nulo.

No exemplo de `Person` classe a seguir, `other` o objeto que é passado para `Person` o construtor de cópia `null`pode ser.

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

No exemplo revisado `Person` a seguir `other` , o objeto que é passado para o construtor de cópia é `PassThroughNonNull` verificado primeiro para nulo no método.

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
            throw new ArgumentNullException("person");
        return person;
    }
}
```