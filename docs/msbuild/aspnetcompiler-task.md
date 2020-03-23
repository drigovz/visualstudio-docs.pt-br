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
ms.openlocfilehash: 8707371fac876586d38f12a797aaee7228b5f729
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634572"
---
# <a name="aspnetcompiler-task"></a>Tarefa AspNetCompiler

A `AspNetCompiler` tarefa envolve *aspnet_compiler.exe*, um utilitário para pré-compilar aplicativos ASP.NET.

## <a name="task-parameters"></a>Parâmetros de tarefa

A tabela a seguir descreve os parâmetros da tarefa `AspNetCompiler`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, o assembly de nome forte permitirá chamadores parcialmente confiáveis.|
|`Clean`|Parâmetro opcional `Boolean`<br /><br /> Se esse parâmetro for `true`, o aplicativo pré-compilado será compilado limpo. Todos os componentes compilados anteriormente serão recompilados. O valor padrão é `false`. Este parâmetro corresponde ao interruptor **-c** em *aspnet_compiler.exe*.|
|`Debug`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, informações de depuração (arquivo .PDB) serão emitidas durante o build. O valor padrão é `false`. Este parâmetro corresponde ao interruptor **-d** em *aspnet_compiler.exe*.|
|`DelaySign`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, o assembly não será totalmente assinado quando for criado.|
|`FixedNames`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, os assemblies compilados receberão nomes fixos.|
|`Force`|Parâmetro opcional `Boolean`<br /><br /> Se esse parâmetro for `true`, a tarefa substituirá o diretório de destino se ele já existir. Os conteúdos existentes serão perdidos. O valor padrão é `false`. Este parâmetro corresponde ao interruptor **-f** em *aspnet_compiler.exe*.|
|`KeyContainer`|Parâmetro `String` opcional.<br /><br /> Especifica um contêiner de chave de nome forte.|
|`KeyFile`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho físico do arquivo de chave de nome forte.|
|`MetabasePath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho completo da metabase do IIS do aplicativo. Esse parâmetro não pode ser combinado com os parâmetros `VirtualPath` ou `PhysicalPath`. Este parâmetro corresponde ao interruptor **-m** em *aspnet_compiler.exe*.|
|`PhysicalPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho físico do aplicativo a ser compilado. Se esse parâmetro estiver ausente, a metabase do IIS será usada para localizar o aplicativo. Este parâmetro corresponde ao interruptor **-p** em *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Parâmetro `String` opcional.<br /><br /> Especifica o TargetFrameworkMoniker indicando qual versão do .NET Framework do *aspnet_compiler.exe* deve ser usada. Aceita apenas monikers do .NET Framework.|
|`TargetPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho físico para o qual o aplicativo é compilado. Se não for especificado, o aplicativo será pré-compilado no local.|
|`Updateable`|Parâmetro `Boolean` opcional.<br /><br /> Se esse parâmetro for `true`, o aplicativo pré-compilado será atualizável.  O valor padrão é `false`. Este parâmetro corresponde ao interruptor **-u** em *aspnet_compiler.exe*.|
|`VirtualPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho virtual do aplicativo a ser compilado. Se `PhysicalPath` for especificado, o caminho físico será usado para localizar o aplicativo. Caso contrário, a metabase do IIS será usada e será considerado que o aplicativo está no site padrão. Este parâmetro corresponde ao **interruptor -v** em *aspnet_compiler.exe*.|

## <a name="remarks"></a>Comentários

Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.ToolTask>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Exemplo

O exemplo de `AspNetCompiler` código a seguir usa a tarefa para pré-compilar um aplicativo ASP.NET.

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
* [Referência de tarefas](../msbuild/msbuild-task-reference.md)
