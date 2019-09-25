---
title: 'CA1812: Evitar classes internas sem instâncias'
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233607"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Evitar classes internas sem instâncias

|||
|-|-|
|NomeDoTipo|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Categoria|Microsoft.Performance|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo interno (de nível de assembly) nunca é instanciado.

## <a name="rule-description"></a>Descrição da regra

Essa regra tenta localizar uma chamada para um dos construtores do tipo e relata uma violação se nenhuma chamada for encontrada.

Os seguintes tipos não são examinados por essa regra:

- Tipos de valor

- Tipos abstratos

- Enumerações

- Delegados

- Tipos de matriz emitidos pelo compilador

- Tipos que não podem ser instanciados e que só [`static`](/dotnet/csharp/language-reference/keywords/static) definem os métodos ([ `Shared` em Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)).

Se você aplicar o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> ao assembly que está sendo analisado, essa regra não sinalizará os tipos marcados como [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` em Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) porque um campo pode ser usado por um assembly Friend.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova o tipo ou adicione o código que o utiliza. Se o tipo contiver `static` apenas métodos, adicione um dos seguintes ao tipo para impedir que o compilador emitisse um construtor de instância pública padrão:

- O `static` modificador C# para tipos que se destinam .NET Framework 2,0 ou posterior.

- Um Construtor privado para tipos que visam .NET Framework versões 1,0 e 1,1.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra. É recomendável suprimir esse aviso nas seguintes situações:

- A classe é criada por meio de métodos de reflexão de associação <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>tardia, como.

- A classe é criada automaticamente pelo tempo de execução ou ASP.NET. Alguns exemplos de classes criadas automaticamente são aquelas que <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> implementam <xref:System.Web.IHttpHandler?displayProperty=fullName>ou.

- A classe é passada como um parâmetro de tipo que tem uma [ `new` restrição](/dotnet/csharp/language-reference/keywords/new-constraint). O exemplo a seguir será sinalizado por CA1812 de regra:

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>Regras relacionadas

- [CA1811: Evitar código particular não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Examinar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Remover locais não utilizados](../code-quality/ca1804-remove-unused-locals.md)