---
title: Metadados de itens conhecidos do MSBuild | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e9320525d770344f131d9e3f04b357de43b5e73
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633090"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadados de itens conhecidos do MSBuild

A tabela a seguir descreve os metadados atribuído a cada item no momento da criação. Em cada exemplo, a seguinte declaração de item foi usada para incluir o arquivo *C:\MyProject\Source\Program.cs* no projeto.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadados do item|DESCRIÇÃO|
|-------------------|-----------------|
|%(FullPath)|Contém o caminho completo do item. Por exemplo:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Contém o diretório raiz do item. Por exemplo:<br /><br /> *C:\\*|
|%(Filename)|Contém o nome do arquivo do item, sem a extensão. Por exemplo:<br /><br /> *Programa*|
|%(Extension)|Contém a extensão de nome de arquivo do item. Por exemplo:<br /><br /> *.cs*|
|%(RelativeDir)|Contém o caminho especificado no atributo `Include`, até a barra invertida final (\\). Por exemplo:<br /><br /> *Origem\\*<br /><br /> Se o atributo `Include` for um caminho completo, `%(RelativeDir)` começará com o diretório raiz `%(RootDir)`.  Por exemplo: <br /><br /> *\\ C:\MyProject\Source*|
|%(Directory)|Contém o diretório do item, sem o diretório raiz. Por exemplo:<br /><br /> *MyProject\\Source\\*|
|%(RecursiveDir)|Se o atributo `Include` contiver o caractere curinga \*\*, esses metadados especificarão a parte do caminho que substitui o caractere curinga. Para saber mais sobre curingas, consulte [Como selecionar os arquivos para compilação](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Se a pasta *C:\MySolution\MyProject\Source\\* contiver o arquivo *Program.cs*, e se o arquivo de projeto contiver este item:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> em seguida, o valor de `%(MyItem.RecursiveDir)` seria *MySolution\MyProject\Source\\* .|
|%(Identity)|O item especificado no atributo `Include`. Por exemplo:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Contém o carimbo de data/hora da última vez que o item foi modificado. Por exemplo:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Contém o carimbo de data/hora de quando o item foi criado. Por exemplo:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Contém o carimbo de data/hora da última vez que o item foi acessado.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Confira também

- [Itens](../msbuild/msbuild-items.md)
- [Envio em lote](../msbuild/msbuild-batching.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
