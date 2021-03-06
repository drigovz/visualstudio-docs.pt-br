---
title: Referência da Tarefa do WPF MSBuild | Microsoft Docs
description: Consulte uma referência de tarefa para o processo de compilação Windows Presentation Foundation (WPF), que estende o MSBuild com tarefas adicionais.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94050565e6c5619781434c7a18307bfbf80b51f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933668"
---
# <a name="wpf-msbuild-task-reference"></a>Referência de tarefas do WPF MSBuild

O processo de build do Windows Presentation Foundation (WPF) estende o Microsoft Build Engine (MSBuild) com um conjunto adicional de tarefas de build, incluindo tarefas para compilar recursos de marcação e o processo.

## <a name="in-this-section"></a>Nesta seção

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Classifica um conjunto de recursos de origem que será inserido em um assembly. Se um recurso não for localizável, ele será inserido no assembly principal do aplicativo; caso contrário, ele será inserido em um assembly satélite.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Gera um assembly se pelo menos uma página XAML em um projeto referencia um tipo declarado localmente nesse projeto. O assembly gerado será removido após concluir o processo de build ou se o processo de build falhar.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Retorna o diretório do tempo de execução de .NET Framework atual.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Converte arquivos de projeto XAML não localizáveis em formato binário compilado.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Executa a compilação de marcação de segundo passo em arquivos XAML que fazem referência a tipos no mesmo projeto.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Mescla os atributos de localização e comentários de um ou mais arquivos de formato binário XAML em um único arquivo para o assembly inteiro.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Insere um ou mais recursos (*. jpg*, *. ico*, *. bmp*, XAML em formato binário e outros tipos de extensão) em um arquivo *. Resources* .

- [UidManager](../msbuild/uidmanager-task.md)

 Verifica, atualiza ou remove os UIDs (identificadores exclusivos) para localizar todos os elementos XAML incluídos nos arquivos XAML de origem.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Adiciona o **\<hostInBrowser />** elemento ao manifesto do aplicativo (*\<projectname> . exe. manifest*) quando um projeto do aplicativo de navegador XAML (XBAP) é compilado.

## <a name="see-also"></a>Confira também

- [MSBuild](../msbuild/msbuild.md)