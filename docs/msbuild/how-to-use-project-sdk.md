---
title: Como fazer referência a um SDK de Projeto do MSBuild | Microsoft Docs
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdcfc9daf2e1e64d61e2f699e0295826894b1920
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136830"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Como usar SDKs de projeto do MSBuild

O MSBuild 15,0 introduziu o conceito do "SDK do projeto", que simplifica o uso de kits de desenvolvimento de software que exigem Propriedades e destinos a serem importados.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Durante a avaliação do projeto, o MSBuild adiciona importações implícitas na parte superior e inferior do arquivo de projeto:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Referenciar um SDK de projeto

Há três maneiras de referenciar um SDK de projeto:

- Use o atributo `Sdk` no elemento `<Project/>`:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Uma importação implícita é adicionada à parte superior e inferior do projeto, conforme discutido anteriormente.
    
    Para especificar uma versão específica do SDK, acrescente-a ao `Sdk` atributo:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

- Use o elemento `<Sdk/>` de nível superior:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Uma importação implícita é adicionada à parte superior e inferior do projeto, conforme discutido anteriormente.
   
   O atributo `Version` não é necessário.

- Use o elemento `<Import/>` em qualquer lugar no projeto:

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   Incluir explicitamente as importações no projeto permite que você tenha controle total sobre a ordem.

   Ao usar o elemento `<Import/>`, você também pode especificar um atributo `Version` opcional. Por exemplo, você pode especificar `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Como os SDKs de projeto são resolvidos

Ao avaliar a importação, o MSBuild resolve dinamicamente o caminho para o SDK do projeto com base no nome e na versão que você especificou.  O MSBuild também tem uma lista de resolvedores de SDK registrados, que são plug-ins que localizam SDKs de projeto em seu computador. Os plug-ins incluem:

- Um resolvedor baseado em NuGet que consulta os feeds de pacotes configurados para pacotes do NuGet que correspondem à ID e à versão do SDK que você especificou.

   Esse resolvedor só estará ativo se você tiver especificado uma versão opcional. Ele pode ser usado para qualquer SDK do projeto personalizado.
   
- Um resolvedor do SDK do .NET que resolve SDKs do MSBuild instalados com o [SDK do .net](/dotnet/core/sdk/).

   Esse resolvedor localiza SDKs de projeto como `Microsoft.NET.Sdk` e `Microsoft.NET.Sdk.Web` que fazem parte do produto.
   
- Um resolvedor padrão que resolve SDKs instalados com o MSBuild.

O resolvedor de SDK baseado em NuGet dá suporte à especificação de uma versão na [global.jsno](/dotnet/core/tools/global-json) arquivo, que permite controlar a versão do SDK do projeto em um único lugar em vez de em cada projeto individual:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Somente uma versão de cada SDK de projeto pode ser usada durante uma compilação. Se você fizer referência a duas versões diferentes do mesmo SDK do projeto, o MSBuild emitirá um aviso. É recomendável **não** especificar uma versão em seus projetos se uma versão for especificada no *global.jsno* arquivo.

## <a name="see-also"></a>Confira também

- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [Personalizar seu build](../msbuild/customize-your-build.md)
- [Pacotes, metadados e estruturas](/dotnet/core/packages)
- [Adições ao formato csproj para .NET Core](/dotnet/core/tools/csproj)
