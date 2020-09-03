---
title: Tarefa XDCMake | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (C++))
- MSBuild (C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c41bfc2015f29cbb73b33df3594b3a3430af3f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77630646"
---
# <a name="xdcmake-task"></a>tarefa XDCMake

Encapsula a ferramenta de documentação XML (*xdcmake.exe*), que mescla arquivos de comentário de documento XML (*. xdc*) em um arquivo *. xml* .

 Um arquivo *. xdc* é criado quando você fornece comentários de documentação em seu código-fonte C++ e compila usando a opção de compilador [/Doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) . Para obter mais informações, [consulte referência de xdcmake](/cpp/build/reference/xdcmake-reference), páginas de propriedades da [ferramenta gerador de documento XML](/cpp/build/reference/xml-document-generator-tool-property-pages)e opção de ajuda de linha de comando (**/?**) para *xdcmake.exe*.

## <a name="remarks"></a>Comentários

 Por padrão, a ferramenta *xdcmake.exe* dá suporte a algumas opções de linha de comando. Opções adicionais terão suporte quando a opção de linha de comando **/old** for especificada.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **XDCMake**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**AdditionalDocumentFile**|Parâmetro opcional de **cadeia de caracteres []** .<br /><br /> Especifica um ou mais arquivos *. xdc* adicionais a serem mesclados.<br /><br /> Para obter mais informações, consulte a descrição de **arquivos de documento adicionais** em [páginas de propriedades da ferramenta gerador de documento XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Consulte também as opções de linha de comando **/Old** e **/FS** para *xdcmake.exe*.|
|**AdditionalOptions**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Uma lista de opções, conforme especificado na linha de comando. Por exemplo,/ \<option1>  / \<option2>  / \<option#> . Use esse parâmetro para especificar opções não representadas por nenhum outro parâmetro da tarefa **XDCMake**.<br /><br /> Para obter mais informações, [consulte referência de xdcmake](/cpp/build/reference/xdcmake-reference), páginas de propriedades da [ferramenta gerador de documento XML](/cpp/build/reference/xml-document-generator-tool-property-pages)e ajuda de linha de comando (**/?**) para *xdcmake.exe*.|
|**DocumentLibraryDependencies**|Parâmetro **booliano** opcional.<br /><br /> Se `true` e o projeto atual tiver uma dependência em um projeto de biblioteca estática (*. lib*) na solução, os arquivos *. xdc* para esse projeto de biblioteca serão incluídos na saída do arquivo *. xml* para o projeto atual.<br /><br /> Para obter mais informações, consulte a descrição de **dependências da biblioteca de documentos** em [páginas de propriedades da ferramenta gerador de documentos XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**OutputFile**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Substitui o nome de arquivo de saída padrão. O nome padrão é derivado do nome do primeiro arquivo *. xdc* que é processado.<br /><br /> Para obter mais informações, consulte a opção **/out \<filename> :** na [referência de xdcmake](/cpp/build/reference/xdcmake-reference). Consulte também as opções de linha de comando **/Old** e **/fo** para *xdcmake.exe*.|
|**ProjectName**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> O nome do projeto atual.|
|**SlashOld**|Parâmetro **booliano** opcional.<br /><br /> Se `true` , habilita opções adicionais de *xdcmake.exe* .<br /><br /> Para obter mais informações, consulte a opção de linha de comando **/Old** para *xdcmake.exe*.|
|**Fontes**|Parâmetro `ITaskItem[]` obrigatório.<br /><br /> Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.|
|**SuppressStartupBanner**|Parâmetro **booliano** opcional.<br /><br /> Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.<br /><br /> Para obter mais informações, consulte a opção **/nologo** na [referência de xdcmake](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o diretório do log de rastreamento.|

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)