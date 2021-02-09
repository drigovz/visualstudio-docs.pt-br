---
title: Glossário do atributo | Ferramenta de teste do desenvolvedor do Microsoft IntelliTest
description: Este artigo fornece uma lista de atributos IntelliTest organizados por namespace e detalhes para os atributos.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2d82e240b33841a390acc5afbdfa1f568797e47e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915778"
---
# <a name="attribute-glossary"></a>Glossário do atributo

## <a name="attributes-by-namespace"></a>Atributos por namespace

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Esse atributo declara que o valor controlado não pode ser **nulo**. Ele pode ser anexado a:

* um **parâmetro** de um método de teste parametrizado

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* um **campo**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* um **tipo**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Ele também pode ser anexado a um assembly de teste, acessório de teste ou método de teste, nesse caso o primeiro argumento deve indicar a qual campo ou tipo as suposições se aplicam. Quando o atributo se aplica a um tipo, ele se aplica a todos os campos com este tipo formal.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Esse atributo marca uma classe que contém *explorações*. É o equivalente a MSTest **TestClassAttribute** (ou ao NUnit **TestFixtureAttribute**). Esse atributo é opcional.

As classes marcadas com [PexClass](#pexclass) devem ser *construíveis por padrão*:

* tipo exportado publicamente
* construtor padrão
* não abstrato

Se a classe não atender a esses requisitos, um erro será relatado e a exploração falhará.

Também é altamente recomendável tornar essas classes **parciais** para que o IntelliTest possa gerar novos testes que fazem parte da classe, mas em um arquivo separado. Essa abordagem resolve muitos problemas devido à [visibilidade](input-generation.md#visibility) e é uma técnica comum em C#.

**Pacotes de teste e categorias adicionais**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Especificando o tipo em teste**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

A classe pode conter métodos anotados com [PexMethod](#pexmethod). O IntelliTest também entende os [métodos de configuração e desmontagem](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Este atributo fornece uma tupla de tipo para instanciar um [teste de unidade parametrizado genérico](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Esse atributo marca um método como um [teste de unidade parametrizado](test-generation.md#parameterized-unit-testing).
O método deve residir em uma classe marcada com o atributo [PexClass](#pexclass).

O IntelliTest gerará testes tradicionais sem parâmetros, que chamam o [teste de unidade parametrizado](test-generation.md#parameterized-unit-testing) com parâmetros diferentes.

O teste de unidade parametrizado:

* deve ser um membro de instância
* deve ser [visível](input-generation.md#visibility) para a classe de teste na qual os testes gerados são colocados de acordo com a [Cascata de configurações](settings-waterfall.md)
* pode conter qualquer número de parâmetros
* pode ser genérico

**Exemplo**

```csharp
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Mais informações](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Este atributo pode ser definido no nível de assembly para substituir os valores de configuração padrão para todas as explorações.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Esse atributo especifica um assembly que está sendo testado pelo projeto de teste atual.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Este atributo é usado para especificar um assembly a ser instrumentado.

**Exemplo**

```csharp
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Este atributo diz ao IntelliTest que ele pode usar um tipo específico para criar uma instância de tipos base (abstratos) ou interfaces.

**Exemplo**

```csharp
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Se esse atributo estiver anexado a um [PexMethod](#pexmethod) (ou a uma [PexClass](#pexclass), ele vai alterar a lógica do IntelliTest padrão que indica quando os testes falham. O teste não será considerado como com falha, mesmo se ele lançar a exceção especificada.

**Exemplo**

O teste a seguir especifica que o construtor de **Stack** pode gerar um **ArgumentOutOfRangeException**:

```csharp
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

O filtro é anexado a um acessório da seguinte maneira (ele também pode ser definido no nível de assembly ou de teste):

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Mais informações](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromAssemblyAttribute)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Mais informações](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeAttribute)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Mais informações](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeUnderTestAttribute)

## <a name="got-feedback"></a>Recebeu comentários?

Poste suas ideias e solicitações de recursos na [Comunidade de Desenvolvedores](https://aka.ms/feedback/suggest?space=8).
