---
title: Tarefa WriteCodeFragment | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee0b819d0387ecbd0bec3a460bf3c63d3122b269
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54796935"
---
# <a name="writecodefragment-task"></a>Tarefa WriteCodeFragment
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Gera um arquivo de código temporário do fragmento de código gerado especificado. Não exclui o arquivo.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `WriteCodeFragment`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`AssemblyAttributes`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Descrição dos atributos para gravação. O item `Include` valor é o nome completo do tipo de atributo, por exemplo, "System.AssemblyVersionAttribute".<br /><br /> Cada metadados são o par nome-valor de um parâmetro, que deve ser do tipo `String`. Alguns atributos só permitem argumentos posicionais de construtor. No entanto, você pode usar esses argumentos em qualquer atributo. Para definir atributos de construtor posicional, use nomes de metadados que se assemelhem "_Parameter1", "_Parameter2" e assim por diante.<br /><br /> Um índice do parâmetro não pode ser ignorado.|  
|`Language`|Parâmetro `String` obrigatório.<br /><br /> Especifica a linguagem do código a ser gerado.<br /><br /> `Language` pode ser qualquer linguagem em que um provedor de CodeDom está disponível, por exemplo, "C#" ou "VisualBasic". O arquivo emitido terá a extensão de nome de arquivo padrão para esse idioma.|  
|`OutputDirectory`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica a pasta de destino para o código gerado, geralmente a pasta intermediária.|  
|`OutputFile`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o caminho do arquivo que foi gerado. Se esse parâmetro for definido usando um nome de arquivo, a pasta de destino será anexada ao nome do arquivo. Se for definido usando uma raiz, a pasta de destino será ignorada.<br /><br /> Se esse parâmetro não for definido, o nome do arquivo de saída será a pasta de destino, um nome de arquivo arbitrário e a extensão de nome de arquivo padrão para o idioma especificado.|  
  
## <a name="remarks"></a>Comentários  
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
