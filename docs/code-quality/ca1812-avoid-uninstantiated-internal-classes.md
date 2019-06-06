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
ms.openlocfilehash: a0d55af3c5522c6bb9aa3ad8a023f070c187ca6f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714261"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Evitar classes internas sem instâncias

|||
|-|-|
|NomeDoTipo|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um tipo interno de (nível de assembly) nunca é instanciado.

## <a name="rule-description"></a>Descrição da regra

Essa regra tenta localizar uma chamada para um dos construtores de tipo e relata uma violação se nenhuma chamada for encontrada.

Os seguintes tipos não são verificados por essa regra:

- Tipos de valor

- Tipos abstratos

- Enumerações

- Delegados

- Tipos de matriz emitidos pelo compilador

- Tipos que não pode ser instanciada e que apenas definem [ `static` ](/dotnet/csharp/language-reference/keywords/static) ([ `Shared` no Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)) métodos.

Se você aplicar a <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> ao assembly que está sendo analisado, essa regra não marcará os tipos que são marcados como [ `internal` ](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` no Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) como um campo pode ser usado por um assembly amigável.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova o tipo ou adicione o código que usa-o. Se o tipo contém apenas `static` métodos, adicione uma das opções a seguir para o tipo para impedir que o compilador emite um construtor de instância pública padrão:

- O `static` modificador para C# tipos de destino [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] ou posterior.

- Um construtor particular para tipos que se destinam a versões do .NET Framework 1.0 e 1.1.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra. É recomendável que você suprimir esse aviso nas seguintes situações:

- A classe é criada por meio de métodos de reflexão de associação tardia como <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- A classe é criada automaticamente pelo tempo de execução ou ASP.NET. Alguns exemplos de classes criadas automaticamente são aqueles que implementam <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> ou <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- A classe é passada como um parâmetro de tipo que tem um [ `new` restrição](/dotnet/csharp/language-reference/keywords/new-constraint). O exemplo a seguir será sinalizado pela regra CA1812:

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

- [CA1811: Evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Revisar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)