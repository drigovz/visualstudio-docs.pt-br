---
title: Elemento PropertyGroup (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb3ae2ba566c42ef1cde10e4a758fe8f9698ed13
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772521"
---
# <a name="propertygroup-element-msbuild"></a>Elemento PropertyGroup (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Contém um conjunto de definidos elementos [Property](../msbuild/property-element-msbuild.md) definidos pelo usuário. Cada elemento `Property` usado em um projeto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] deve ser um filho de um elemento `PropertyGroup`.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Condição|Atributo opcional.<br /><br /> Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Property](../msbuild/property-element-msbuild.md)|Elemento opcional.<br /><br /> Um nome de propriedade definida pelo usuário, que contém o valor da propriedade. Pode ser que não haja nenhum ou mais de um elemento *Property* em um elemento `PropertyGroup`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Projeto](../msbuild/project-element-msbuild.md)|Elemento raiz necessário de um arquivo de projeto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como definir propriedades com base em uma condição. Neste exemplo, se o valor da propriedade `CompileConfig` é for `DEBUG`, as propriedades `Optimization`, `Obfuscate` e `OutputPath` dentro do elemento `PropertyGroup` são definidos.  
  
```  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)  
 [Propriedades MSBuild](msbuild-properties1.md)
