---
title: Metadados de itens conhecidos do MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: abf45460ec924aea7a6c1c18244aa7661c52d42f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790181"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadados de itens conhecidos do MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
A tabela a seguir descreve os metadados atribuído a cada item no momento da criação. Em cada exemplo, a seguinte declaração de item foi usada para incluir o arquivo `C:\MyProject\Source\Program.cs` no projeto.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Metadados de item|Descrição|  
|-------------------|-----------------|  
|%(FullPath)|Contém o caminho completo do item. Por exemplo:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Contém o diretório raiz do item. Por exemplo:<br /><br /> `C:\`|  
|%(Filename)|Contém o nome do arquivo do item, sem a extensão. Por exemplo:<br /><br /> `Program`|  
|%(Extension)|Contém a extensão de nome de arquivo do item. Por exemplo:<br /><br /> `.cs`|  
|%(RelativeDir)|Contém o caminho especificado no atributo `Include`, até a barra invertida final (\\). Por exemplo:<br /><br /> `Source\`|  
|%(Directory)|Contém o diretório do item, sem o diretório raiz. Por exemplo:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Se o atributo `Include` contiver o caractere curinga \*\*, esses metadados especificarão a parte do caminho que substitui o caractere curinga. Para obter mais informações sobre curingas, consulte [Como selecionar os arquivos a serem compilados](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Se a pasta *C:\MySolution\MyProject\Source\\* contiver o arquivo Program.cs e se o arquivo de projeto contiver este item:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> em seguida, o valor de `%(MyItem.RecursiveDir)` seria *MySolution\MyProject\Source\\*.|  
|%(Identity)|O item especificado no atributo `Include`. Por exemplo:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Contém o carimbo de data/hora da última vez que o item foi modificado. Por exemplo:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Contém o carimbo de data/hora de quando o item foi criado. Por exemplo:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Contém o carimbo de data/hora da última vez que o item foi acessado.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Consulte também  
 [Itens](../msbuild/msbuild-items.md)   
 [Envio em lote](../msbuild/msbuild-batching.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)
