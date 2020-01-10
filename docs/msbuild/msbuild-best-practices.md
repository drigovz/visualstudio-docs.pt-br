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
ms.openlocfilehash: b1aee1a6ae3abc06846523df9470ad75d316a50b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592081"
---
# <a name="msbuild-best-practices"></a>Melhores práticas do MSBuild
Recomendamos as seguintes práticas recomendadas para escrever scripts MSBuild:

- Os valores de propriedade padrão são mais facilmente tratados usando o atributo `Condition` e não declarando uma propriedade cujo valor padrão pode ser substituído na linha de comando. Por exemplo, use

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Evite curingas ao selecionar itens. Em vez disso, especifique os arquivos explicitamente. Isso torna mais fácil controlar os erros que podem ocorrer quando você adiciona ou exclui arquivos.

## <a name="see-also"></a>Veja também
- [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)
