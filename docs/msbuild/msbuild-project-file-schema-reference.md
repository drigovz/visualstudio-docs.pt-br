---
title: Referência do esquema de arquivo de projeto MSBuild | Microsoft Docs
description: Consulte uma tabela que lista todos os elementos de esquema XML do MSBuild com seus atributos disponíveis e elementos filho.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3451101d6ab2483960731281763167c0cd1629c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918982"
---
# <a name="msbuild-project-file-schema-reference"></a>Referência de esquema de arquivos de projeto do MSBuild

Fornece uma tabela de todos os elementos de esquema XML do MSBuild com seus atributos disponíveis e elementos filho.

 O MSBuild usa arquivos de projeto para instruir o mecanismo de compilação sobre o que compilar e como compilá-lo. Arquivos de projeto do MSBuild são arquivos XML que aderem ao esquema XML do MSBuild. Esta seção documenta o arquivo de definição de esquema XML (*. xsd*) para o MSBuild.

O link do esquema em um arquivo de projeto do MSBuild não é necessário no Visual Studio 2017 e posterior. Se presente, ele deve ser ` http://schemas.microsoft.com/developer/msbuild/2003` independente da versão do Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Elementos do esquema XML do MSBuild

 A tabela a seguir lista todos os elementos do esquema XML do MSBuild junto com seus elementos filho e atributos.

|Elemento|Elementos filho|Atributos|
|-------------|--------------------|----------------|
|[Escolher elemento (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> Quando|--|
|[Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condição<br /><br /> Project|
|[Elemento ImportGroup](../msbuild/importgroup-element.md)|Importar|Condição|
|[Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condição<br /><br /> Excluir<br /><br /> Incluir<br /><br /> Remover|
|[Elemento ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Condição|
|[Elemento dogroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Condição|
|[Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Condição|
|[Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condição<br /><br /> ExecuteTargets|
|[Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Elemento Output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condição<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Elemento Parameter](../msbuild/parameter-element.md)|--|Saída<br /><br /> ParameterType<br /><br /> Obrigatório|
|[Elemento ParameterGroup](../msbuild/parametergroup-element.md)|*Parâmetro*|--|
|[Elemento Project (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importar<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Destino<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> SDK<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condição|
|[Elemento PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Propriedade*|Condição|
|[Elemento SDK (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nome<br /><br /> Versão|
|[Elemento de destino (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Tarefa*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condição<br /><br /> DependsOnTargets<br /><br /> Entradas<br /><br /> KeepDuplicateOutputs<br /><br /> Nome<br /><br /> Saídas<br /><br /> Retornos|
|[Elemento Task de Target (MSBuild)](../msbuild/task-element-msbuild.md)|Saída|Condição<br /><br /> ContinueOnError<br /><br /> *Parâmetro*|
|[Elemento Task de UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dados*|Avaliar|
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Tarefa|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condição<br /><br /> TaskFactory<br /><br /> TaskName|
|[Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condição|

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Condições](../msbuild/msbuild-conditions.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
