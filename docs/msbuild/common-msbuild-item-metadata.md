---
title: Metadados de item do MSBuild comuns | Microsoft Docs
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
ms.openlocfilehash: 1c715c16782733a08bb617a464c1aa9510d35b54
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425950"
---
# <a name="common-msbuild-item-metadata"></a>Metadados comuns de item do MSBuild

A tabela a seguir descreve os metadados de item opcionais que têm significado para alguns SDKs ou destinos do MSBuild, mas que não são definidos por padrão para cada item. Você pode defini-los para influenciar o comportamento da compilação, mas somente se os arquivos de destino ou SDK que você está usando o reconhecem.

| Metadados do item | SDKs | Descrição |
|---------------| ------- | -------------|
|% (Link)| Todos |O sistema de projeto do Visual Studio usa `Link` metadados (se presente) para alterar o que aparece na árvore do projeto; você pode colocar um arquivo em uma estrutura de pastas lógica diferente em **Gerenciador de soluções**.<br />Além disso, a `AssignTargetPath` tarefa examina `Link` para determinar de onde o diretório de saída copiar um arquivo, se for um dos itens copiados.|
|% (LinkBase)| SDK do .Net Core | Usado para definir a pasta a ser usada para os `Link` metadados de grupos de itens. |

## <a name="see-also"></a>Confira também

- [Propriedades de projeto comuns do MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Itens de projeto comuns do MSBuild](../msbuild/common-msbuild-project-items.md)
- [Metadados de itens conhecidos do MSBuild](msbuild-well-known-item-metadata.md)