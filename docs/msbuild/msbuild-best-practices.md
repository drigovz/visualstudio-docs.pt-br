---
title: Práticas recomendadas do MSBuild | Microsoft Docs
description: Saiba mais sobre as práticas recomendadas para escrever scripts do MSBuild, como usar atributos de condição e não usar curingas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2742324f737a4e70221e3cbe4c78cff56fa7e7ca
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047656"
---
# <a name="msbuild-best-practices"></a>Melhores práticas do MSBuild

Recomendamos as seguintes práticas recomendadas para escrever scripts MSBuild:

- Os valores de propriedade padrão são mais facilmente tratados usando o atributo `Condition` e não declarando uma propriedade cujo valor padrão pode ser substituído na linha de comando. Por exemplo, use

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Em geral, evite o uso de curingas ao selecionar itens. Em vez disso, especifique os arquivos explicitamente. Isso ocorre porque, na maioria dos tipos de projetos, o MSBuild expande curingas em vários momentos, como ao adicionar ou remover itens, o que pode levar a um comportamento inesperado. Uma exceção a isso está em projetos de SDK do .NET Core estilo, que processam caracteres curinga corretamente.

## <a name="see-also"></a>Veja também

- [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)
