---
title: Tarefa BscMake | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acf9c0df17ec0e1bb97c1426d5d312f616de0a8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747382"
---
# <a name="bscmake-task"></a>Tarefa BscMake
> [!IMPORTANT]
> O BscMake não é mais usado pelo IDE do Visual Studio. Desde o Visual Studio 2008, as informações de procura são armazenadas automaticamente em um arquivo *.sdf* na pasta *Solution*.

 Encapsula a ferramenta Utilitário de Manutenção de Informações de Procura da Microsoft (*bscmake.exe*).  A ferramenta *bscmake.exe* compila um arquivo de informações de procura ( *.bsc*) com base nos arquivos do navegador de origem ( *.sbr*) que são criados durante a compilação. Use o **Pesquisador de Objetos** para exibir um arquivo *.bsc*. Para obter mais informações, confira [Referência do BSCMAKE](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parâmetros
 A tabela a seguir descreve os parâmetros da tarefa **BscMake**. A maioria dos parâmetros de tarefa corresponde a uma opção de linha de comando.

|Parâmetro|Descrição|
|---------------|-----------------|
|**AdditionalOptions**|Parâmetro **String** opcional.<br /><br /> Uma lista de opções, conforme especificado na linha de comando. Por exemplo, /\<option1> /\<option2> /\<option#>. Use esse parâmetro para especificar opções não representadas por nenhum outro parâmetro da tarefa **BscMake**.<br /><br /> Para obter mais informações, confira as opções em [Opções do BSCMAKE](/cpp/build/reference/bscmake-options).|
|**OutputFile**|Parâmetro **String** opcional.<br /><br /> Especifica um nome de arquivo que substitui o nome de arquivo de saída padrão.<br /><br /> Para obter mais informações, confira a opção **/o** em [Opções do BSCMAKE](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, ele forçará um build não incremental. Um build completo não incremental ocorre, independentemente da existência de um arquivo *.bsc* e impede o truncamento de arquivos *.sbr*.<br /><br /> Para obter mais informações, confira a opção **/n** em [Opções do BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Sources**|Parâmetro opcional **ITaskItem[]** .<br /><br /> Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.|
|**SuppressStartupBanner**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.<br /><br /> Para obter mais informações, confira a opção **/NOLOGO** em [Opções do BSCMAKE](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory**|Parâmetro **String** opcional.<br /><br /> Especifica o diretório do log de rastreamento.|

## <a name="see-also"></a>Consulte também
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)