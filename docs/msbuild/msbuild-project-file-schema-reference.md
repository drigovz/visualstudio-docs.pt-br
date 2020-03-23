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
ms.openlocfilehash: 824a6f562638edb04854431c437289f2741c46d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263068"
---
# <a name="msbuild-project-file-schema-reference"></a>Referência de esquema de arquivos de projeto do MSBuild

Fornece uma tabela de todos os elementos do Esquema MSBuild XML com seus atributos disponíveis e elementos infantis.

 O MSBuild usa arquivos de projeto para instruir o mecanismo de compilação sobre o que construir e como construí-lo. Os arquivos do projeto MSBuild são arquivos XML que aderem ao esquema MSBuild XML. Esta seção documenta o arquivo de definição de esquema XML *(.xsd)* para MSBuild.

O link de esquema em um arquivo de projeto MSBuild não é necessário no Visual Studio 2017 e posterior. Se estiver presente, ` http://schemas.microsoft.com/developer/msbuild/2003` deve ser independente da versão do Visual Studio.

## <a name="msbuild-xml-schema-elements"></a>Elementos do esquema XML do MSBuild

 A tabela a seguir lista todos os elementos do esquema MSBuild XML, juntamente com seus elementos e atributos filhos.

|Elemento|Elementos filho|Atributos|
|-------------|--------------------|----------------|
|[Escolha o elemento (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> Quando|--|
|[Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Condição<br /><br /> Project|
|[Elemento ImportGroup](../msbuild/importgroup-element.md)|Importar|Condição|
|[Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Condição<br /><br /> Excluir<br /><br /> Incluir<br /><br /> Remover|
|[Elemento ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Condição|
|[Elemento ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Condição|
|[Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Condição|
|[Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Condição<br /><br /> ExecuteTargets|
|[Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Elemento de saída (MSBuild)](../msbuild/output-element-msbuild.md)|--|Condição<br /><br /> NomeItem<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Elemento Parameter](../msbuild/parameter-element.md)|--|Saída<br /><br /> ParameterType<br /><br /> Obrigatório|
|[Elemento parameterGroup](../msbuild/parametergroup-element.md)|*Parâmetro*|--|
|[Elemento do projeto (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importar<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Destino<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[Elemento ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Condição|
|[Elemento PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Propriedade*|Condição|
|[Elemento Sdk (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Nome<br /><br /> Versão|
|[Elemento-alvo (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Tarefa*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Condição<br /><br /> DependsOnTargets<br /><br /> Entradas<br /><br /> KeepDuplicateOutputs<br /><br /> Nome<br /><br /> outputs<br /><br /> Retornos|
|[Elemento de tarefa do Target (MSBuild)](../msbuild/task-element-msbuild.md)|Saída|Condição<br /><br /> ContinueOnError<br /><br /> *Parâmetro*|
|[Elemento de tarefa do UsingTask (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dados*|Avaliar|
|[Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Tarefa|AssemblyFile<br /><br /> AssemblyName<br /><br /> Condição<br /><br /> TaskFactory<br /><br /> TaskName|
|[Quando elemento (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Condição|

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Condições](../msbuild/msbuild-conditions.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
