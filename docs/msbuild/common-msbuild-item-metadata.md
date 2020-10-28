---
title: Metadados de item do MSBuild comuns | Microsoft Docs
description: Saiba mais sobre os metadados de item opcionais que têm significado para alguns SDKs ou destinos do MSBuild, mas não são definidos por padrão para cada item.
ms.custom: SEO-VS-2020
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 152967fb99442b58d96016e10d8899b57ef35bf6
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796584"
---
# <a name="common-msbuild-item-metadata"></a>Metadados de itens comuns do MSBuild

A tabela a seguir descreve os metadados de item opcionais que têm significado para alguns SDKs ou destinos do MSBuild, mas que não são definidos por padrão para cada item. Você pode defini-los para influenciar o comportamento da compilação, mas somente se os arquivos de destino ou SDK que você está usando o reconhecem.

| Metadados do item | SDKs | Descrição |
|---------------| ------- | -------------|
|% (Link)| Tudo |O sistema de projeto do Visual Studio usa `Link` metadados (se presente) para alterar o que aparece na árvore do projeto; você pode colocar um arquivo em uma estrutura de pastas lógica diferente em **Gerenciador de soluções** .<br />Além disso, a `AssignTargetPath` tarefa examina `Link` para determinar de onde o diretório de saída copiar um arquivo, se for um dos itens copiados.|
|% (LinkBase)| SDK do .Net Core | Usado para definir a pasta a ser usada para os `Link` metadados de grupos de itens. |

## <a name="see-also"></a>Veja também

- [Propriedades de projeto comuns do MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Itens de projeto comuns do MSBuild](../msbuild/common-msbuild-project-items.md)
- [Metadados de itens conhecidos do MSBuild](msbuild-well-known-item-metadata.md)