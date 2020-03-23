---
title: Introdução ao IntelliTest
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 113233c985053cfe838f385a36ec59cc211bfcb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591652"
---
# <a name="get-started-with-microsoft-intellitest"></a>Introdução ao Microsoft IntelliTest

* Se esta for a primeira vez que você trabalha com o IntelliTest:
  * assista ao [vídeo do Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * leia esta [visão geral na MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * leia nossa [documentação](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Fazer perguntas sobre [Stack Overflow](https://stackoverflow.com/questions/tagged/intellitest)
* Leia o restante deste manual de referência
* Imprima esta página para referência rápida

## <a name="important-attributes"></a>Atributos importantes

* [PexClass](attribute-glossary.md#pexclass) marca um tipo que contém **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) marca um **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) marca um parâmetro não nulo

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) associa um projeto de teste a um projeto
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) especifica um assembly para instrumentar

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a>Importantes classes de ajudantes estáticos

* [PexAssume](static-helper-classes.md#pexassume) avalia suposições (filtragem de entrada)
* [PexAssert](static-helper-classes.md#pexassert) avalia declarações
* [PexChoose](static-helper-classes.md#pexchoose) gera novas opções (entradas adicionais)
* [PexObserve](static-helper-classes.md#pexobserve) registra valores dinâmicos para os testes gerados

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>Recebeu comentários?

Poste suas ideias e solicitações de recursos na [Comunidade de Desenvolvedores](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
