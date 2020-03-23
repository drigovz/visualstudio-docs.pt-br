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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630646"
---
# <a name="xdcmake-task"></a>tarefa XDCMake

Envolve a ferramenta Documentação XML *(xdcmake.exe),* que mescla arquivos xml de comentário de documento *(.xdc)* em um arquivo *.xml.*

 Um arquivo *.xdc* é criado quando você fornece comentários de documentação em seu código fonte C++ e compila usando a opção [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) compilor. Para obter mais informações, consulte [XDCMake reference](/cpp/build/reference/xdcmake-reference), [XML Document Generator Tool páginas de propriedade](/cpp/build/reference/xml-document-generator-tool-property-pages)e opção de ajuda de linha de comando (**/?**) para *xdcmake.exe*.

## <a name="remarks"></a>Comentários

 Por padrão, a ferramenta *xdcmake.exe* suporta algumas opções de linha de comando. Opções adicionais terão suporte quando a opção de linha de comando **/old** for especificada.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **XDCMake**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**AdditionalDocumentFile**|Parâmetro opcional **string[].**<br /><br /> Especifica um ou mais arquivos *.xdc* adicionais para mesclar.<br /><br /> Para obter mais informações, consulte a descrição **Arquivos adicionais de documentos** nas páginas de propriedade da ferramenta de gerador de documentos [XML](/cpp/build/reference/xml-document-generator-tool-property-pages). Veja também as opções de linha de comando **/old** e **/Fs** para *xdcmake.exe*.|
|**AdditionalOptions**|Parâmetro opcional **string.**<br /><br /> Uma lista de opções, conforme especificado na linha de comando. Por exemplo, /\<option1> /\<option2> /\<option#>. Use esse parâmetro para especificar opções não representadas por nenhum outro parâmetro da tarefa **XDCMake**.<br /><br /> Para obter mais informações, consulte [XDCMake reference](/cpp/build/reference/xdcmake-reference), [XML Document Generator Tool páginas de propriedade](/cpp/build/reference/xml-document-generator-tool-property-pages)e ajuda de linha de comando (**/?**) para *xdcmake.exe*.|
|**DocumentLibraryDependencies**|Parâmetro **booleano** opcional.<br /><br /> Se `true` e o projeto atual tiver uma dependência de um projeto de biblioteca estática *(.lib)* na solução, os arquivos *.xdc* para esse projeto de biblioteca estão incluídos na saída de arquivo *.xml* para o projeto atual.<br /><br /> Para obter mais informações, consulte a descrição **Dependências da Biblioteca de Documentos** nas páginas de propriedade da ferramenta de gerador de documentos [XML](/cpp/build/reference/xml-document-generator-tool-property-pages).|
|**Outputfile**|Parâmetro opcional **string.**<br /><br /> Substitui o nome de arquivo de saída padrão. O nome padrão é derivado do nome do primeiro arquivo *.xdc* que é processado.<br /><br /> Para saber mais, confira a opção **/out:\<nomedoarquivo>** em [Referência XDCMake](/cpp/build/reference/xdcmake-reference). Veja também as opções de linha de comando **/old** e **/Fo** para *xdcmake.exe*.|
|**Projectname**|Parâmetro opcional **string.**<br /><br /> O nome do projeto atual.|
|**SlashOld**|Parâmetro **booleano** opcional.<br /><br /> Se `true`, habilitar opções *xdcmake.exe* adicionais.<br /><br /> Para obter mais informações, consulte a opção **/old** command-line para *xdcmake.exe*.|
|**Fontes**|Parâmetro `ITaskItem[]` obrigatório.<br /><br /> Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.|
|**SuppressStartupBanner**|Parâmetro **booleano** opcional.<br /><br /> Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.<br /><br /> Para obter mais informações, consulte a opção **/nologo** em [referência XDCMake](/cpp/build/reference/xdcmake-reference).|
|**TrackerLogDirectory**|Parâmetro opcional **string.**<br /><br /> Especifica o diretório do log de rastreamento.|

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)