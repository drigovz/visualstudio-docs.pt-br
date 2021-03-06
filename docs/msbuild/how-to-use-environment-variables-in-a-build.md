---
title: Como usar variáveis de ambiente em um build | Microsoft Docs
description: Saiba como acessar variáveis de ambiente em arquivos de projeto do MSBuild e usar variáveis de ambiente para definir opções de compilação sem modificar o arquivo de projeto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c7c81f36d37d071593a013067f661451b8916caa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914183"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Como usar variáveis de ambiente em um build

Quando você compila projetos, geralmente é necessário definir opções de build usando informações que não estão no arquivo de projeto ou nos arquivos que compõem seu projeto. Normalmente, essas informações são armazenadas em variáveis de ambiente.

## <a name="reference-environment-variables"></a>Referenciar variáveis de ambiente

 Todas as variáveis de ambiente estão disponíveis para o arquivo de projeto Microsoft Build Engine (MSBuild) como propriedades.

> [!NOTE]
> Se o arquivo de projeto contiver uma definição explícita de uma propriedade que tem o mesmo nome que uma variável de ambiente, a propriedade no arquivo de projeto substituirá os valores de uma variável de ambiente.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Para usar uma variável de ambiente em um projeto MSBuild

- Faça referência à variável de ambiente da mesma maneira que faria com uma variável declarada em seu arquivo de projeto. Por exemplo, o código a seguir faz referência à variável de ambiente BIN_PATH:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  Você pode usar um atributo `Condition` para fornecer um valor padrão para uma propriedade se a variável de ambiente não foi definida.

#### <a name="to-provide-a-default-value-for-a-property"></a>Para fornecer um valor padrão de uma propriedade

- Use um atributo `Condition` em uma propriedade para definir o valor somente se a propriedade não tiver nenhum valor. Por exemplo, o seguinte código define a propriedade `ToolsPath` como *c:\tools* somente se a variável de ambiente `ToolsPath` não está definida:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > Os nomes de propriedade não diferenciam maiúsculas de minúsculas então `$(ToolsPath)` e `$(TOOLSPATH)` fazem referência à mesma variável de ambiente ou propriedade.

## <a name="example"></a>Exemplo

 O arquivo de projeto a seguir usa variáveis de ambiente para especificar o local dos diretórios.

```xml
<Project DefaultTargets="FakeBuild">
    <PropertyGroup>
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">
            C:\Tools
        </ToolsPath>
    </PropertyGroup>
    <Target Name="FakeBuild">
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [MSBuild](../msbuild/msbuild.md)
- [propriedades MSBuild](../msbuild/msbuild-properties.md)
- [Como: compilar os mesmos arquivos de origem com opções diferentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
