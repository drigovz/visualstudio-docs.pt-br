---
title: Tarefa RC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 156de08e8bd0ed2a8cadd0653facfa99d352cb20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915582"
---
# <a name="rc-task"></a>tarefa RC
Encapsula a ferramenta do Compilador de Recursos do Microsoft Windows, *rc.exe*. A tarefa **RC** compila recursos como cursores, ícones, bitmaps, caixas de diálogo e fontes em um arquivo de recurso (*.res*). Para saber mais, confira [Compilador de recursos](https://docs.microsoft.com/windows/desktop/menurc/resource-compiler).
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa RC. A maioria dos parâmetros de tarefa e alguns conjuntos de parâmetros correspondem a uma opção de linha de comando.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Parâmetro **String[]** opcional.<br /><br /> Adiciona um diretório à lista de diretórios que são pesquisados para arquivos de inclusão.<br /><br /> Para saber mais, confira a opção **/I** em [Usar RC (a linha de comando de RC)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**AdditionalOptions**|Parâmetro **String** opcional.<br /><br /> Uma lista de opções de linha de comando; por exemplo /\<option1> /\<option2> /\<option#>. Use esse parâmetro para especificar opções de linha de comando não representadas por nenhum outro parâmetro de tarefa **RC**.<br /><br /> Para saber mais, consulte as opções em [Usar RC (a linha de comando de RC)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**Cultura**|Parâmetro **String** opcional.<br /><br /> Especifica uma ID de localidade que representa a cultura usada nos recursos.<br /><br /> Para saber mais, confira a opção **/l** em [Usar RC (a linha de comando de RC)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**IgnoreStandardIncludePath**|Parâmetro **Boolean** opcional.<br /><br /> Se for `true`, impede que o compilador de recurso verifique a variável de ambiente INCLUDE ao procurar por arquivos de cabeçalho ou arquivos de recurso.<br /><br /> Para saber mais, confira a opção **/x** em [Usar RC (a linha de comando de RC)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**NullTerminateStrings**|Parâmetro **Boolean** opcional.<br /><br /> Se for `true`, termina em nulo todas as cadeias de caracteres na tabela de cadeia de caracteres.<br /><br /> Para saber mais, confira a opção **/n** em [Usar RC (a linha de comando de RC)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**PreprocessorDefinitions**|Parâmetro **String[]** opcional.<br /><br /> Defina um ou mais símbolos de pré-processador para o compilador de recurso. Especifique uma lista de símbolos de macro.<br /><br /> Para saber mais, confira a opção **/d** em [Usar RC (a linha de comando de RC)](http://go.microsoft.com/fwlink/?LinkId=155730). Consulte também **UndefinePreprocessorDefinitions** nessa tabela.|  
|**ResourceOutputFileName**|Parâmetro **String** opcional.<br /><br /> Especifica o nome do arquivo de recurso. Especifica um nome de arquivo de recurso.<br /><br /> Para saber mais, confira a opção **/fo** em [Usar RC (a linha de comando de RC)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**ShowProgress**|Parâmetro **Boolean** opcional.<br /><br /> Se for `true`, exibe mensagens que relatam o andamento do compilador.<br /><br /> Para saber mais, confira a opção **/v** em [Usar RC (a linha de comando de RC)](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**Source**|Parâmetro `ITaskItem[]` obrigatório.<br /><br /> Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.|  
|**SuppressStartupBanner**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.<br /><br /> Para obter mais informações, digite a opção de linha de comando **/?**  e, em seguida, confira a opção **/nologo**.|  
|**TrackerLogDirectory**|Parâmetro **String** opcional.<br /><br /> Especifica o diretório de log de rastreamento.|  
|**UndefinePreprocessorDefinitions**|Cancela a definição de um símbolo de pré-processador.<br /><br /> Para saber mais, confira a opção **/u** em [Usar RC (a linha de comando de RC)](http://go.microsoft.com/fwlink/?LinkId=155730). Consulte também **PreprocessorDefinitions** nessa tabela.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)