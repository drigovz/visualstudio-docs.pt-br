---
title: MSBuild .targets Files | Microsoft Docs
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3faa9ca73592722a950f9914437884c33122070e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633350"
---
# <a name="msbuild-targets-files"></a>Arquivos .targets do MSBuild

O MSBuild inclui vários arquivos *.targets* que contêm itens, propriedades, alvos e tarefas para cenários comuns. Esses arquivos são automaticamente importados para a maioria dos arquivos de projeto do Visual Studio para simplificar a manutenção e a legibilidade.

 Normalmente, os projetos importam um ou mais arquivos *.targets* para definir o processo de build. Por exemplo, um projeto C# criado pelo Visual Studio importará *alvos Microsoft.CSharp.que* importa *microsoft.common.targets*. O projeto C# em si definirá os itens e propriedades específicos para esse projeto, mas as regras de compilação padrão para um projeto C# são definidas nos arquivos *importados .targets.*

 O valor `$(MSBuildToolsPath)` especifica o caminho desses arquivos *.targets* comuns. Se `ToolsVersion` for 4.0, os arquivos estiverem no seguinte local: * \<WindowsInstallationPath\\>\Microsoft.NET\Framework\v4.0.30319*

> [!NOTE]
> Para obter informações sobre como criar seus próprios destinos, consulte [Destinos](../msbuild/msbuild-targets.md). Para obter informações sobre como usar o elemento `Import` para inserir um arquivo de projeto em outro arquivo de projeto, confira [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) e [Como usar o mesmo destino em vários arquivos de projeto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Arquivos .targets comuns

| Arquivo *.targets* | Descrição |
|---------------------------------| - |
| *Microsoft.Common.targets* | Define as etapas no processo de construção padrão para projetos Visual Basic e C#.<br /><br /> Importado pelos arquivos *Microsoft.CSharp.targets* e *Microsoft.VisualBasic.targets*, que incluem a seguinte instrução: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Define as etapas no processo de build padrão de projetos do Visual C#.<br /><br /> Importado pelos arquivos de projeto do Visual C# (*.csproj*), que incluem a seguinte instrução: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Define as etapas no processo de build padrão de projetos do Visual Basic.<br /><br /> Importados por arquivos de projeto Visual Basic *(.vbproj),* que incluem a seguinte declaração:`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets* é um arquivo definido pelo usuário que fornece personalizações a projetos em um diretório. Esse arquivo é importado automaticamente de *Microsoft.Common.targets*, a menos que a propriedade **ImportDirectoryBuildTargets** seja definida como **false**. Para obter mais informações, confira [Personalizar seu build](customize-your-build.md).

## <a name="see-also"></a>Confira também

- [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
