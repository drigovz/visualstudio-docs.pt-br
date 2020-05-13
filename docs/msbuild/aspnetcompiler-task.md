---
title: Usando a tarefa AspNetCompiler para pré-compilar aplicativos ASP.NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 072d1b94c552b3aca34a1573e5d6545628f6568e
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167326"
---
# <a name="aspnetcompiler-task"></a>Tarefa AspNetCompiler

A `AspNetCompiler` tarefa encapsula *aspnet_compiler. exe*, um utilitário para pré-compilar ASP.NET Applications.

## <a name="task-parameters"></a>Parâmetros de tarefa

A tabela a seguir descreve os parâmetros da tarefa `AspNetCompiler`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, o assembly de nome forte permitirá chamadores parcialmente confiáveis.|
|`Clean`|Parâmetro opcional `Boolean`<br /><br /> Se esse parâmetro for `true`, o aplicativo pré-compilado será compilado limpo. Todos os componentes compilados anteriormente serão recompilados. O valor padrão é `false`. Esse parâmetro corresponde à opção **-c** em *aspnet_compiler. exe*.|
|`Debug`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, informações de depuração (arquivo .PDB) serão emitidas durante o build. O valor padrão é `false`. Esse parâmetro corresponde à opção **-d** em *aspnet_compiler. exe*.|
|`DelaySign`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, o assembly não será totalmente assinado quando for criado.|
|`FixedNames`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, os assemblies compilados receberão nomes fixos.|
|`Force`|Parâmetro opcional `Boolean`<br /><br /> Se esse parâmetro for `true`, a tarefa substituirá o diretório de destino se ele já existir. Os conteúdos existentes serão perdidos. O valor padrão é `false`. Esse parâmetro corresponde à opção **-f** em *aspnet_compiler. exe*.|
|`KeyContainer`|Parâmetro `String` opcional.<br /><br /> Especifica um contêiner de chave de nome forte.|
|`KeyFile`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho físico do arquivo de chave de nome forte.|
|`MetabasePath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho completo da metabase do IIS do aplicativo. Esse parâmetro não pode ser combinado com os parâmetros `VirtualPath` ou `PhysicalPath`. Esse parâmetro corresponde à opção **-m** em *aspnet_compiler. exe*.|
|`PhysicalPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho físico do aplicativo a ser compilado. Se esse parâmetro estiver ausente, a metabase do IIS será usada para localizar o aplicativo. Esse parâmetro corresponde à opção **-p** em *aspnet_compiler. exe*.|
|`TargetFrameworkMoniker`|Parâmetro `String` opcional.<br /><br /> Especifica o TargetFrameworkMoniker que indica qual .NET Framework versão do *aspnet_compiler. exe* deve ser usada. Aceita apenas monikers do .NET Framework.|
|`TargetPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho físico para o qual o aplicativo é compilado. Se não for especificado, o aplicativo será pré-compilado no local.|
|`Updateable`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, o aplicativo pré-compilado será atualizável.  O valor padrão é `false`. Esse parâmetro corresponde à opção **-u** em *aspnet_compiler. exe*.|
|`VirtualPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho virtual do aplicativo a ser compilado. Se `PhysicalPath` for especificado, o caminho físico será usado para localizar o aplicativo. Caso contrário, a metabase do IIS será usada e será considerado que o aplicativo está no site padrão. Esse parâmetro corresponde à opção **-v** em *aspnet_compiler. exe*.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Exemplo

O exemplo de código a seguir `AspNetCompiler` usa a tarefa para pré-compilar um aplicativo ASP.net.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="PrecompileWeb">
        <AspNetCompiler
            VirtualPath="/MyWebSite"
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"
            TargetPath="c:\precompiledweb\MyWebSite\"
            Force="true"
            Debug="true"
        />
    </Target>
</Project>
```

## <a name="see-also"></a>Confira também

* [Tarefas](../msbuild/msbuild-tasks.md)
* [Referência de tarefa](../msbuild/msbuild-task-reference.md)
