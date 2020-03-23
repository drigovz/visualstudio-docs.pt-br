---
title: Referência da Tarefa do WPF MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70d994e32b717ff566a2e38acee732c7525d1bb0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630841"
---
# <a name="wpf-msbuild-task-reference"></a>Referência de tarefas do WPF MSBuild

O processo de build do Windows Presentation Foundation (WPF) estende o Microsoft Build Engine (MSBuild) com um conjunto adicional de tarefas de build, incluindo tarefas para compilar recursos de marcação e o processo.

## <a name="in-this-section"></a>Nesta seção

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Classifica um conjunto de recursos de origem que será inserido em um assembly. Se um recurso não for localizável, ele será inserido no assembly principal do aplicativo; caso contrário, ele será inserido em um assembly satélite.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Gera um conjunto se pelo menos uma página XAML em um projeto faz referência a um tipo que é declarado localmente nesse projeto. O assembly gerado será removido após concluir o processo de build ou se o processo de build falhar.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Retorna o diretório do tempo de execução atual do .NET Framework.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Converte arquivos de projeto XAML não localizados em formato binário compilado.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Realiza compilação de marcação de segunda passagem em arquivos XAML que referenciam tipos no mesmo projeto.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Mescla os atributos de localização e os comentários de um ou mais arquivos de formato binário XAML em um único arquivo para toda a montagem.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Incorpora um ou mais recursos *(.jpg*, *.ico,* *.bmp*, XAML em formato binário e outros tipos de extensão) em um arquivo *.resources.*

- [UidManager](../msbuild/uidmanager-task.md)

 Verifica, atualiza ou remove identificadores exclusivos (UIDs), a fim de localizar todos os elementos XAML que estão incluídos nos arquivos XAML de origem.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Adiciona o ** \<elemento hostInBrowser />** ao manifesto do aplicativo*\<(projectname>.exe.manifest)* quando um projeto XAML Browser Application (XBAP) é construído.

## <a name="see-also"></a>Confira também

- [MSBuild](../msbuild/msbuild.md)