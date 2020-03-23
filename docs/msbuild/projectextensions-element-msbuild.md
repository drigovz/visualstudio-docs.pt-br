---
title: Elemento ProjectExtensions (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94f2d88aa19bf01ebe6f25c7d80772c812abcc59
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632960"
---
# <a name="projectextensions-element-msbuild"></a>Elemento ProjectExtensions (MSBuild)

Permite que os arquivos do projeto MSBuild contenham informações não-MSBuild. Qualquer coisa `ProjectExtensions` dentro de um elemento será ignorada pelo MSBuild.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Sintaxe

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

 Nenhum

### <a name="child-elements"></a>Elementos filho

 Nenhum

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto MSBuild. |

## <a name="remarks"></a>Comentários

 Apenas `ProjectExtensions` um elemento pode ser usado em um projeto MSBuild.

## <a name="example"></a>Exemplo

 O exemplo de código a seguir mostra informações do ambiente de desenvolvimento integrado que estão sendo armazenado em um elemento `ProjectExtensions`.

```xml
<ProjectExtensions>
    <VSIDE>
        <External>
            <!--
            Raw XML passed to the IDE by an external source
            -->
        </External>
    </VSIDE>
</ProjectExtensions>
```

## <a name="see-also"></a>Confira também

- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
