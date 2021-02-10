---
title: Elemento Sdk (MSBuild) | Microsoft Docs
description: Saiba mais sobre sintaxe, atributos e elementos para o elemento do SDK do MSBuild, que faz referência a um SDK de projeto do MSBuild.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd5f66cc6500a3320e0da962985f5b7fff1e86dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937895"
---
# <a name="sdk-element-msbuild"></a>Elemento Sdk (MSBuild)

Faz referência a um SDK de projeto do MSBuild.

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
| [Projeto](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto do MSBuild. |

## <a name="see-also"></a>Confira também

- [Como referenciar um SDK de projeto do MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
