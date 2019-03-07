---
title: Práticas recomendadas do MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae4390632dc9c1ce0cb47d5733145739719ae87c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617347"
---
# <a name="msbuild-best-practices"></a>Melhores práticas do MSBuild
Recomendamos as seguintes práticas recomendadas para escrever scripts MSBuild:

-   Os valores de propriedade padrão são mais facilmente tratados usando o atributo `Condition` e não declarando uma propriedade cujo valor padrão pode ser substituído na linha de comando. Por exemplo, use

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

-   Evite curingas ao selecionar itens. Em vez disso, especifique os arquivos explicitamente. Isso torna mais fácil controlar os erros que podem ocorrer quando você adiciona ou exclui arquivos.

## <a name="see-also"></a>Consulte também
- [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)
