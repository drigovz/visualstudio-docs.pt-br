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
ms.openlocfilehash: c810e166ef6f04befdbf7a5d18fe20bb65b8a299
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425375"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadados de itens conhecidos do MSBuild

Os metadados do item são valores anexados aos itens. Alguns são atribuídos pelo MSBuild a itens quando os itens são criados, mas você também pode definir quaisquer metadados necessários. Alguns valores de metadados definidos pelo usuário têm significado para MSBuild, tarefas de tarefas específicas ou SDKs, como o SDK do .NET.

A primeira tabela neste artigo descreve os metadados atribuídos a cada item na criação. A tabela a seguir mostra alguns metadados opcionais que têm significado para o MSBuild, que você pode definir para controlar o comportamento da compilação. Em cada exemplo, a seguinte declaração de item foi usada para incluir o arquivo *C:\MyProject\Source\Program.cs* no projeto.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadados do item|Descrição|
|-------------------|-----------------|
|%(FullPath)|Contém o caminho completo do item. Por exemplo:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Contém o diretório raiz do item. Por exemplo:<br /><br /> *&\\*|
|%(Filename)|Contém o nome do arquivo do item, sem a extensão. Por exemplo:<br /><br /> *Programa*|
|%(Extension)|Contém a extensão de nome de arquivo do item. Por exemplo:<br /><br /> *. cs*|
|%(RelativeDir)|Contém o caminho especificado no atributo `Include`, até a barra invertida final (\\). Por exemplo:<br /><br /> *Fonte\\*<br /><br /> Se o `Include` atributo for um caminho completo, `%(RelativeDir)` começa com o diretório raiz `%(RootDir)` .  Por exemplo: <br /><br /> *C:\MyProject\Source\\*|
|%(Directory)|Contém o diretório do item, sem o diretório raiz. Por exemplo:<br /><br /> *MyProject\\Source\\*|
|%(RecursiveDir)|Se o atributo `Include` contiver o caractere curinga \*\*, esses metadados especificarão a parte do caminho que substitui o caractere curinga. Para obter mais informações sobre curingas, consulte [como: selecionar os arquivos a serem compilados](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Se a pasta *C:\MySolution\MyProject\Source \\ * contiver o arquivo *Program.cs*, e se o arquivo de projeto contiver este item:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> em seguida, o valor de `%(MyItem.RecursiveDir)` seria *MySolution\MyProject\Source\\*.|
|%(Identity)|O item especificado no `Include` atributo. Por exemplo:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Contém o carimbo de data/hora da última vez que o item foi modificado. Por exemplo:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Contém o carimbo de data/hora de quando o item foi criado. Por exemplo:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Contém o carimbo de data/hora da última vez que o item foi acessado.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Confira também

- [Metadados comuns de item do MSBuild](common-msbuild-item-metadata.md)
- [Itens](../msbuild/msbuild-items.md)
- [Separação em lotes](../msbuild/msbuild-batching.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
