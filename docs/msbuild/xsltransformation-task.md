---
title: Tarefa XslTransformation | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa de XslTransform para transformar uma entrada XML usando um XSLT e uma saída para um dispositivo ou arquivo de saída.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f779fc5d222fdd0985adef203f0bb20fc601a429
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847940"
---
# <a name="xsltransformation-task"></a>Tarefa XslTransformation

Transformações um XML de entrada usando um XSLT ou XSLT compilado e saídas para um arquivo ou um dispositivo de saída.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `XslTransformation`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`OutputPaths`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos de saída para a transformação XML.|
|`Parameters`|Parâmetro `String` opcional.<br /><br /> Especifica os parâmetros para o documento de entrada XSLT.  Forneça o XML bruto que contém cada parâmetro como `<Parameter Name="" Value="" Namespace="" />` .|
|`XmlContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XML como uma cadeia de caracteres.|
|`XmlInputPaths`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os arquivos de entrada XML.|
|`XslCompiledDllPath`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o XSLT compilado.|
|`XslContent`|Parâmetro `String` opcional.<br /><br /> Especifica a entrada XSLT como uma cadeia de caracteres.|
|`XslInputPath`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o arquivo de entrada XSLT.|

## <a name="remarks"></a>Comentários

 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

No exemplo a seguir, um arquivo de transformação XSL *Transform. XSLT* é usado para modificar o arquivo XML `$(XmlInputFileName)` . O XML transformado é gravado no `$(IntermediateOutputPath)output.xml` . A transformação XSL usa `$(Parameter1)` como um parâmetro de entrada.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Confira também

- [Parâmetros XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
