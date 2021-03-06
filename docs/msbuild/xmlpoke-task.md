---
title: Tarefa XmlPoke | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa xmlfazer para definir valores conforme especificado por uma consulta XPath em um arquivo XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d829376fcece336434fa5e816c725d5be61ac1a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956029"
---
# <a name="xmlpoke-task"></a>Tarefa XmlPoke

Define os valores conforme especificado por uma consulta de XPath em um arquivo XML.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `XmlPoke`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`Namespaces`|Parâmetro `String` opcional.<br /><br /> Especifica os namespaces para prefixos de consulta do XPath. `Namespaces` é um snippet XML que consiste em elementos `Namespace` com atributos `Prefix` e `Uri`. O atributo `Prefix` especifica o prefixo para associar ao namespace especificado no atributo `Uri`. Não use um `Prefix` vazio.|
|`Query`|Parâmetro `String` opcional.<br /><br /> Especifica a consulta do XPath.|
|`Value`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o valor a ser inserido no caminho especificado.|
|`XmlInputPath`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica a entrada XML como um caminho de arquivo.|

## <a name="remarks"></a>Comentários

 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

Aqui está um sample.xml para modificar:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

Neste exemplo, se você quiser modificar `/Package/mp:PhoneIdentity/PhoneProductId`, use

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` aqui é usado como um prefixo de namespace artificial para o namespace padrão.

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
