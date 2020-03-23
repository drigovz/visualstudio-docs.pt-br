---
title: Como usar o mesmo destino em vários arquivos de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b7b36a829e2e406ecd3f10ba3a2b588c6f7df25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633753"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Como usar o mesmo destino em vários arquivos de projeto

Se você tiver sido autor de vários arquivos do projeto MSBuild, você pode ter descoberto que você precisa usar as mesmas tarefas e alvos em diferentes arquivos de projeto. Em vez de incluir a descrição completa dessas tarefas ou destinos em todos os arquivos de projeto, você pode salvar um destino em um arquivo de projeto separado e, em seguida, importar o projeto para qualquer outro projeto que precise usar o destino.
## <a name="use-the-import-element"></a>Usar o elemento Import

 O elemento `Import` é usado para inserir um arquivo de projeto em outro arquivo de projeto. O arquivo do projeto que está sendo importado deve ser um arquivo de projeto MSBuild válido e conter XML bem formado. O atributo `Project` especifica o caminho para o arquivo de projeto importado. Para obter mais `Import` informações sobre o elemento, consulte [Import element (MSBuild)](../msbuild/import-element-msbuild.md).
O elemento `Import` é usado para inserir um arquivo de projeto em outro arquivo de projeto. O arquivo do projeto que está sendo importado deve ser um arquivo de projeto MSBuild válido e conter XML bem formado. O atributo `Project` especifica o caminho para o arquivo de projeto importado. Para obter mais `Import` informações sobre o elemento, consulte [Import element (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Para importar um projeto

1. Defina, no arquivo de projeto para o qual está sendo realizada a importação, todas as propriedades e itens que são usados como parâmetros para propriedades e itens no projeto importado.

2. Use o elemento `Import` para importar o projeto. Por exemplo: 

     `<Import Project="MyCommon.targets"/>`

3. Após o elemento `Import`, defina todas as propriedades e itens que devem substituir as definições padrão de propriedades e itens no projeto importado.

## <a name="order-of-evaluation"></a>Ordem de avaliação

 Quando o MSBuild `Import` atinge um elemento, o projeto importado é efetivamente inserido `Import` no projeto de importação no local do elemento. Portanto, o local do elemento `Import` pode afetar os valores de propriedades e de itens. É importante entender as propriedades e os itens que são definidos pelo projeto importado e as propriedades e itens usados pelo projeto importado.

 Quando o projeto é compilado, todas as propriedades são avaliadas primeiro, seguidas dos itens. Por exemplo, o XML a seguir define o arquivo de projeto importado *MyCommon.targets:*

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 O XML a seguir define *MyApp.proj*, que importa *MyCommon.targets*:

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 Quando o projeto é compilado, a seguinte mensagem é exibida:

 `Name="MyCommon"`

 Como o projeto é importado `Name` após a propriedade ter sido definida `Name` no *MyApp.proj*, a definição de in *MyCommon.targets* substitui a definição no *MyApp.proj*. Se o projeto é importado antes de a propriedade Name ser definida, o build exibe a seguinte mensagem:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Usar a abordagem a seguir ao importar projetos

1. Defina, no arquivo de projeto, todas as propriedades e itens que são usados como parâmetros para propriedades e itens no projeto importado.

2. Importe o projeto.

3. Defina, no arquivo de projeto, todas as propriedades e itens que devem substituir as definições padrão de propriedades e itens no projeto importado.

## <a name="example"></a>Exemplo

 O exemplo de código a seguir mostra o arquivo *MyCommon.targets* que o segundo exemplo de código importa. O arquivo *.targets* avalia propriedades do projeto de importação para configurar a compilação.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example"></a>Exemplo

 O exemplo de código a seguir importa o arquivo *MyCommon.targets.*

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>Confira também

- [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)
- [Destinos](../msbuild/msbuild-targets.md)
