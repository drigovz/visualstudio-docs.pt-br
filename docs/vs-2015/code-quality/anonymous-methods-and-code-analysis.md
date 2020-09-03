---
title: Métodos anônimos e análise de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652219"
---
# <a name="anonymous-methods-and-code-analysis"></a>Métodos anônimos e análise de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um *método anônimo* é um método sem nome. Os métodos anônimos são usados com mais frequência para passar um bloco de código como um parâmetro delegado.

 Este tópico explica como a análise de código trata avisos e métricas associados a métodos anônimos.

## <a name="anonymous-methods-declared-in-a-member"></a>Métodos anônimos declarados em um membro
 Os avisos e as métricas para um método anônimo que é declarado em um membro, como um método ou acessador, são associados ao membro que declara o método. Eles não estão associados ao membro que chama o método.

 Por exemplo, na classe a seguir, todos os avisos encontrados na declaração de **anonymousMethod** devem ser gerados em **Method1** e não **Method2**.

```vb

      Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass

    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End SubSub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End SubEnd Class
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
 Os avisos e as métricas para um método anônimo que é declarado como uma atribuição embutida para um campo são associados ao construtor. Se o campo for declarado como `static` ( `Shared` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), os avisos e as métricas serão associados ao construtor da classe; caso contrário, eles serão associados ao construtor da instância.

 Por exemplo, na classe a seguir, todos os avisos encontrados na declaração de **anonymousMethod1** serão gerados no construtor padrão da **classe**gerado implicitamente. Enquanto isso, os encontrados em **anonymousMethod2** serão aplicados no construtor de classe gerado implicitamente.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5

Sub Method1()
    anonymousMethod1(10)
    anonymousMethod2(10)
End SubEnd Class
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

 Uma classe pode conter um método anônimo embutido que atribui um valor a um campo que tem vários construtores. Nesse caso, os avisos e as métricas são associados a todos os construtores, a menos que esse construtor se encadeia a outro construtor na mesma classe.

 Por exemplo, na classe a seguir, todos os avisos encontrados na declaração de **anonymousMethod** devem ser gerados em relação à **classe (int)** e à **classe (cadeia de caracteres)** , mas não à **classe ()**.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass

Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)
value > 5

SubNew()
    New(CStr(Nothing))
End SubSub New(ByVal a As Integer)
End SubSub New(ByVal a As String)
End SubEnd Class
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

 Embora isso possa parecer inesperado, isso ocorre porque o compilador gera um método exclusivo para cada Construtor que não se encadea a outro construtor. Devido a esse comportamento, qualquer violação que ocorra em **anonymousMethod** deve ser suprimida separadamente. Isso também significa que, se um novo Construtor for introduzido, os avisos que foram suprimidos anteriormente em relação à **classe (int)** e à **classe (cadeia de caracteres)** também deverão ser suprimidos em relação ao novo construtor.

 Você pode contornar esse problema de uma das duas maneiras. Você pode declarar **anonymousMethod** em um Construtor comum que todos os construtores se encadeadom. Ou você pode declará-lo em um método de inicialização que é chamado por todos os construtores.

## <a name="see-also"></a>Consulte Também
 [Analisando a qualidade do código gerenciado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
