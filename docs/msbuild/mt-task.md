---
title: Tarefa MT | Microsoft Docs
description: Saiba mais sobre os parâmetros e opções de linha de comando da tarefa MSBuild MT, que encapsula a ferramenta de manifesto da Microsoft, mt.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (C++), MT task
- MT task (MSBuild (C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a023c58e528b2cda74fa42fcce46fd9c39059459
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905424"
---
# <a name="mt-task"></a>tarefa MT

Encapsula a ferramenta de manifesto da Microsoft, *mt.exe*. Para saber mais, confira [Mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **MT**. A maioria dos parâmetros de tarefa e alguns conjuntos de parâmetros correspondem a uma opção de linha de comando.

> [!NOTE]
> A documentação da *mt.exe* usa um hífen (**-**) como prefixo para opções de linha de comando, mas este tópico usa uma barra (**/**). Qualquer um desses prefixos é aceitável.

|Parâmetro|Descrição|
|---------------|-----------------|
|**AdditionalManifestFiles**|Parâmetro opcional de **cadeia de caracteres []** .<br /><br /> Especifica o nome de um ou mais arquivos de manifesto.<br /><br /> Para saber mais, confira a opção **/manifest** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AdditionalOptions**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Uma lista de opções de linha de comando. Por exemplo,/ \<option1>  / \<option2>  / \<option#> . Use esse parâmetro para especificar opções de linha de comando não representadas por nenhum outro parâmetro da tarefa **MT**.<br /><br /> Para saber mais, confira [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica os valores de atributo do elemento **assemblyIdentity** do manifesto. Especifique uma lista delimitada por vírgula, em que o primeiro componente é o valor do `name` atributo, seguido por um ou mais pares de nome/valor que têm o formato *\<attribute name> =<ATTRIBUTE_VALUE>*.<br /><br /> Para saber mais, confira a opção **/identity** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ComponentFileName**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o nome da biblioteca de vínculo dinâmico a ser criada com base nos arquivos *.rgs* ou *.tlb*. Esse parâmetro é necessário ao especificar os parâmetros de tarefa MT **RegistrarScriptFile** ou **TypeLibraryFile**.<br /><br /> Para saber mais, confira a opção **/dll** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**DependencyInformationFile**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o arquivo das informações de dependência usado pelo Visual Studio para rastrear as informações de dependência de compilação para a ferramenta de manifesto.|
|**EmbedManifest**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, incorpora o arquivo de manifesto no assembly. Se `false`, cria um arquivo de manifesto autônomo.|
|**EnableDPIAwareness**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, adiciona as informações de manifesto que marcam o aplicativo como com reconhecimento de DPI. O registro de um aplicativo com reconhecimento de DPI melhora a aparência da interface do usuário de forma consistente em uma ampla variedade de configurações de exibição com alto DPI.<br /><br /> Para saber mais, confira [Alto DPI](/windows/desktop/win7devguide/high-dpi).|
|**GenerateCatalogFiles**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, gera arquivos de definição de catálogo (*.cdf*).<br /><br /> Para saber mais, confira a opção **/makecdfs** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**GenerateCategoryTags**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, faz com que as marcas de categoria sejam geradas. Se esse parâmetro for `true`, o parâmetro de tarefa **ManifestFromManagedAssemblyMT** também deverá ser especificado.<br /><br /> Para saber mais, confira a opção **/category** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> A entrada do manifesto por meio de um recurso do tipo RT_MANIFEST que tem o identificador especificado. Especificar um recurso do formulário, \<file> [; [ #] \<resource_id> ], em que o \<resource_id> parâmetro opcional é um número não negativo de 16 bits.<br /><br /> Se nenhum `resource_id` for especificado, o valor padrão (1) CREATEPROCESS_MANIFEST_RESOURCE será usado.<br /><br /> Para saber mais, confira a opção **/inputresource** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestFromManagedAssembly**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Gera um manifesto do assembly gerenciado especificado.<br /><br /> Para saber mais, confira a opção **/managedassemblyname** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestToIgnore**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> (Não usado).|
|**OutputManifestFile**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o nome do manifesto de saída. Se esse parâmetro for omitido e somente um manifesto for operado, esse manifesto será modificado.<br /><br /> Para saber mais, confira a opção **/out** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**OutputResourceManifests**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> A saída do manifesto por meio de um recurso do tipo RT_MANIFEST que tem o identificador especificado. O recurso está no formato, \<file> [; [ #] \<resource_id> ], em que o \<resource_id> parâmetro opcional é um número não negativo de 16 bits.<br /><br /> Se nenhum `resource_id` for especificado, o valor padrão (1) CREATEPROCESS_MANIFEST_RESOURCE será usado.<br /><br /> Para saber mais, confira a opção **/outputresource** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**RegistrarScriptFile**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o nome do arquivo de script de registrador (*.rgs*) a ser usado para suporte ao manifesto COM sem registro.<br /><br /> Para saber mais, confira a opção **/rgs** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ReplacementsFile**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o arquivo que contém valores para cadeias de caracteres substituíveis no arquivo registrador (*.rgs*).<br /><br /> Para saber mais, confira a opção **/replacements** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ResourceOutputFileName**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o arquivo de recurso de saída usado para inserir o manifesto na saída do projeto.|
|**Fontes**|Parâmetro `ITaskItem[]` opcional.<br /><br /> Especifica uma lista de arquivos de manifesto de origem separados por espaços.<br /><br /> Para saber mais, confira a opção **/manifest** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressDependencyElement**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, gera um manifesto sem elementos de dependência. Se esse parâmetro for `true`, o parâmetro de tarefa **ManifestFromManagedAssemblyMT** também deverá ser especificado.<br /><br /> Para saber mais, confira a opção **/nodependency** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressStartupBanner**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.<br /><br /> Para saber mais, confira a opção **/nologo** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**TrackerLogDirectory**|Parâmetro `String` opcional.<br /><br /> Especifica o diretório intermediário em que os logs de rastreamento para essa tarefa são armazenados.|
|**TypeLibraryFile**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o nome do arquivo de biblioteca de tipos (*.tlb*). Ao especificar esse parâmetro, especifique também o parâmetro de tarefa **ComponentFileNameMT**.<br /><br /> Para saber mais, confira a opção **/tlb** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**UpdateFileHashes**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, calcula o valor de hash dos arquivos no caminho especificado pelo parâmetro de tarefa **UpdateFileHashesSearchPathMT** e, em seguida, atualiza o valor do atributo **hash** do elemento de **arquivo** do manifesto usando o valor calculado.<br /><br /> Para saber mais, confira a opção **/hashupdate** em [Mt.exe](/windows/desktop/SbsCs/mt-exe). Consulte também o parâmetro **UpdateFileHashesSearchPath** nesta tabela.|
|**UpdateFileHashesSearchPath**|Parâmetro `String` opcional.<br /><br /> Especifica o caminho de pesquisa a ser usado quando os hashes de arquivo são atualizados. Use esse parâmetro com o parâmetro de tarefa **UpdateFileHashesMT**.<br /><br /> Para obter mais informações, consulte o parâmetro **UpdateFileHashes** nesta tabela.|
|**VerboseOutput**|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, exibe informações de depuração detalhadas.<br /><br /> Para saber mais, confira a opção **/verbose** em [Mt.exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
