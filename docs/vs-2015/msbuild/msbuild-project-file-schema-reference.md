---
title: Referência do esquema de arquivo de projeto MSBuild | Microsoft Docs
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
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 847fa53acad63cec151222521ed8f85090c52080
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158862"
---
# <a name="msbuild-project-file-schema-reference"></a>Referência do esquema de arquivos de projeto do MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fornece uma tabela de todos os elementos [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do esquema XML com elementos filho e atributos disponíveis.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] usa arquivos de projeto para instruir o mecanismo de build sobre o que e como compilar. Os arquivos de projeto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] são arquivos XML que seguem o esquema XML [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Esta seção documenta o arquivo de definição do esquema XML (.xsd) para [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>Elementos do esquema XML do MSBuild  
 A tabela a seguir lista todos os elementos [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] de esquema XML junto com seus atributos e elementos filho.  
  
|Elemento|Elementos filho|Atributos|  
|-------------|--------------------|----------------|  
|[Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> Quando|--|  
|[Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condição<br /><br /> Project|  
|[Elemento Import](../msbuild/importgroup-element.md)|Importar|Condição|  
|[Elemento item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condição<br /><br /> Excluir<br /><br /> Incluir<br /><br /> Remover|  
|[Elemento ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Condição|  
|[Elemento ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Condição|  
|[Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Condição|  
|[Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condição<br /><br /> ExecuteTargets|  
|[Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Elemento Output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condição<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Elemento Parameter](../msbuild/parameter-element.md)|--|Saída<br /><br /> ParameterType<br /><br /> Obrigatório|  
|[Elemento Parameter](../msbuild/parametergroup-element.md)|*Parâmetro*|--|  
|[Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importar<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Destino<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condição|  
|[Elemento PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Propriedade*|Condição|  
|[Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Tarefa*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condição<br /><br /> DependsOnTargets<br /><br /> Entradas<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Saídas<br /><br /> Retornos|  
|[Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md)|Saída|Condição<br /><br /> ContinueOnError<br /><br /> *Parâmetro*|  
|[Elemento TaskBody (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dados*|Avaliar|  
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condição<br /><br /> TaskFactory<br /><br /> TaskName|  
|[Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condição|  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de tarefa](../msbuild/msbuild-task-reference.md)   
 [Situações](../msbuild/msbuild-conditions.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
