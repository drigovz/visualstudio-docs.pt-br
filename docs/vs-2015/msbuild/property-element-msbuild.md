---
title: Elemento Property (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eefe0160328f1eb6b3fe841742547efe8be50ec1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158270"
---
# <a name="property-element-msbuild"></a>Elemento Property (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contém um nome e valor de propriedade definidos pelo usuário. Cada propriedade usada em um projeto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] deve ser especificada como filho de um elemento `PropertyGroup`.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Condition`|Atributo opcional.<br /><br /> Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento de agrupamento para propriedades.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é opcional.  
  
 Esse texto especifica o valor da propriedade e pode conter XML.  
  
## <a name="remarks"></a>Comentários  
 Nomes de propriedade estão limitados a apenas a caracteres ASCII. Valores de propriedades são referenciados no projeto, colocando o nome da propriedade entre "`$(`" e "`)`". Por exemplo, `$(builddir)\classes` resolveria "build\classes" se a propriedade `builddir` tinha o valor `build`. Para obter mais informações sobre propriedades, consulte [Propriedades do MSBuild](msbuild-properties1.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir define a propriedade `Optimization` para `false` e a propriedade `DefaultVersion` para `1.0` se a propriedade `Version` estiver vazia.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Consulte Também
[Propriedades do MSBuild](msbuild-properties1.md)  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)
