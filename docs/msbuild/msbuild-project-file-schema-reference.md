---
title: Referência do esquema de arquivo de projeto MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: def9edb232a37bc58a56ffd1ec9a16bcb1b75092
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590313"
---
# <a name="msbuild-project-file-schema-reference"></a>Referência de esquema de arquivos de projeto do MSBuild
Fornece uma tabela de todos os elementos [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do esquema XML com elementos filho e atributos disponíveis.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usa arquivos de projeto para instruir o mecanismo de build sobre o que e como compilar. Os arquivos de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] são arquivos XML que seguem o esquema XML [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Esta seção documenta o arquivo de definição de esquema XML ( *.xsd*) para o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="msbuild-xml-schema-elements"></a>Elementos do esquema XML do MSBuild
 A tabela a seguir lista todos os elementos [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de esquema XML junto com seus atributos e elementos filho.

|Elemento|Child elements|{1&gt;{2&gt;Atributos&lt;2}&lt;1}|
|-------------|--------------------|----------------|
|[Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|
|[Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condição<br /><br /> Projeto do|
|[Elemento ImportGroup](../msbuild/importgroup-element.md)|Importar|Condição|
|[Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condição<br /><br /> Excluir<br /><br /> Incluir<br /><br /> Remover|
|[Elemento ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Condição|
|[Elemento ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Condição|
|[Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Condição|
|[Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condição<br /><br /> ExecuteTargets|
|[Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Escolha<br /><br /> ItemGroup<br /><br /> GrupoPropriedade|--|
|[Elemento Output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condição<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Elemento Parameter](../msbuild/parameter-element.md)|--|Saída<br /><br /> ParameterType<br /><br /> Necessário|
|[Elemento ParameterGroup](../msbuild/parametergroup-element.md)|*Parâmetro*|--|
|[Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md)|Escolha<br /><br /> Importar<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> GrupoPropriedade<br /><br /> Destino<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condição|
|[Elemento PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Property*|Condição|
|[Elemento Sdk (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Name<br /><br /> Versão do|
|[Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Tarefa*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condição<br /><br /> DependsOnTargets<br /><br /> Entradas<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Saídas<br /><br /> Retorna|
|[Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md)|Saída|Condição<br /><br /> ContinueOnError<br /><br /> *Parâmetro*|
|[Elemento TaskBody (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dados*|Avaliar o|
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condição<br /><br /> TaskFactory<br /><br /> TaskName|
|[Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)|Escolha<br /><br /> ItemGroup<br /><br /> GrupoPropriedade|Condição|

## <a name="see-also"></a>Veja também
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Condições](../msbuild/msbuild-conditions.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
