---
title: Elemento ItemMetadata (MSBuild) | Microsoft Docs
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
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e3d9f72abfd095288b50ab8de9b9bc3eae4cc51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162370"
---
# <a name="itemmetadata-element-msbuild"></a>Elemento ItemMetadata (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contém uma chave de metadados de item definida pelo usuário, que contém o valor de metadados do item. Um item pode ter qualquer número de pares de chave-valor de metadados.  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|DESCRIÇÃO|  
|---------------|-----------------|  
|`Condition`|Atributo opcional.<br /><br /> Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|DESCRIÇÃO|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Um elemento definido pelo usuário que define as entradas para o processo de build.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é opcional.  
  
 Esse texto Especifica o valor de metadados do item, que pode ser texto ou XML.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como adicionar metadados de `Culture` com o valor `fr` ao item `CSFile`.  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Veja também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Itens](../msbuild/msbuild-items.md)
