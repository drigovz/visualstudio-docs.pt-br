---
title: Avisos de análise de código do método anônimo
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd5053f3774c7a92d16690883a0845ba7bae32db
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008927"
---
# <a name="anonymous-methods-and-code-analysis"></a>Métodos anônimos e análise de código

Uma *método anônimo* é um método que não tem nome. Métodos anônimos são usados com mais frequência para passar um bloco de código como um parâmetro delegado. Este artigo explica como a análise de código lida com os avisos e as métricas para métodos anônimos.

## <a name="anonymous-methods-declared-in-a-member"></a>Métodos anônimos, declarados em um membro

Avisos e as métricas para um método anônimo que é declarada em um membro, como um método ou um acessador, são associadas com o membro que declara o método. Eles não são associados com o membro que chama o método.

Por exemplo, na classe, todos os avisos que são encontrados na declaração de **anonymousMethod** deve ser gerado em relação a **Method1** e não **Method2**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass
    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End Sub
    Sub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>Métodos anônimos embutidos

Avisos e as métricas para um método anônimo que é declarado como uma atribuição de embutido para um campo são associadas com o construtor. Se o campo é declarado como `static` (`Shared` no Visual Basic), os avisos e as métricas estão associadas com o construtor de classe. Caso contrário, eles são associados com o construtor de instância.

Por exemplo, na classe, todos os avisos que são encontrados na declaração de **anonymousMethod1** será gerado com o construtor padrão gerado implicitamente da **classe**. Os avisos que são encontrados no **anonymousMethod2** serão aplicadas contra o construtor de classe gerada implicitamente.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass
    Dim anonymousMethod1 As ADelegate = Function(ByVal value As Integer) value > 5
    Shared anonymousMethod2 As ADelegate = Function(ByVal value As Integer) value > 5

    Sub Method1()
        anonymousMethod1(10)
        anonymousMethod2(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

Uma classe pode conter um método anônimo embutido que atribui um valor a um campo que tem vários construtores. Nesse caso, avisos e as métricas estão associadas a todos os construtores, a menos que esse construtor encadeia outro construtor na mesma classe.

Por exemplo, na classe, todos os avisos que são encontrados na declaração de **anonymousMethod** deve ser gerado em relação a **Class(int)** e **Class(string)**, mas não em relação ao **Class ()**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass

    Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5

    SubNew()
        New(CStr(Nothing))
    End Sub

    Sub New(ByVal a As Integer)
    End Sub

    Sub New(ByVal a As String)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

Os avisos são gerados em relação a construtores, porque o compilador gera um método exclusivo para cada construtor que não é vinculado a outro construtor. Devido a esse comportamento, qualquer violação que isso ocorre na **anonymousMethod** deve ser suprimida separadamente. Isso também significa que, se um novo construtor é introduzida, os avisos que anteriormente eram suprimidos contra **Class(int)** e **Class(string)** também devem ser suprimidos contra o novo construtor.

Você pode contornar esse problema em uma das duas maneiras:

- Declarar **anonymousMethod** em um construtor comuns que todas as cadeia de construtores.
- Declarar **anonymousMethod** em um método de inicialização que é chamado por todos os construtores.

## <a name="see-also"></a>Consulte também

- [Analisando a qualidade do código gerenciado](../code-quality/code-analysis-for-managed-code-overview.md)