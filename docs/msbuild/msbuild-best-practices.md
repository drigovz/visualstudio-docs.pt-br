---
title: Práticas recomendadas do MSBuild | Microsoft Docs
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
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263143"
---
# <a name="msbuild-best-practices"></a>Melhores práticas do MSBuild

Recomendamos as seguintes práticas recomendadas para escrever scripts MSBuild:

- Os valores de propriedade padrão são mais facilmente tratados usando o atributo `Condition` e não declarando uma propriedade cujo valor padrão pode ser substituído na linha de comando. Por exemplo, use

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Em geral, evite o uso de curingas quando selecionar itens. Em vez disso, especifique os arquivos explicitamente. Isso ocorre porque, na maioria dos tipos de projetos, o MSBuild expande curingas em vários momentos, como ao adicionar ou remover itens, o que pode levar a comportamentos inesperados. Uma exceção para isso está em projetos no estilo .NET Core SDK, que processam curingas corretamente.

## <a name="see-also"></a>Confira também

- [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)
