---
title: Elemento Sdk (MSBuild) | Microsoft Docs
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a704744032c5dea70246463a816ba8e1f5c84e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632466"
---
# <a name="sdk-element-msbuild"></a>Elemento Sdk (MSBuild)

Faz referência a um SDK do projeto MSBuild.

 \<Project> \<Sdk>

## <a name="syntax"></a>Sintaxe

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Name`|Atributo obrigatório.<br /><br /> O nome do SDK do projeto.|
|`Version`|Atributo opcional.<br /><br /> A versão do SDK do projeto|

### <a name="child-elements"></a>Elementos filho

 Nenhum.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto MSBuild. |

## <a name="see-also"></a>Confira também

- [Como: Referenciar um SDK do projeto MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
