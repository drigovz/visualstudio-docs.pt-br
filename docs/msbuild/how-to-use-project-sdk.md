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
ms.openlocfilehash: 74ccc29417cdee7a9f93c39509c0f7d06a5c72ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826465"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Como usar SDKs de projeto do MSBuild

O MSBuild 15.0 introduziu o conceito do "projeto SDK", que simplifica o uso de kits de desenvolvimento de software que exigem propriedades e metas a serem importadas.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Durante a avaliação do projeto, o MSBuild adiciona importações implícitas na parte superior e inferior do arquivo do projeto:

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

    Uma importação implícita é adicionada à parte superior e inferior do projeto, como discutido anteriormente.
    
    Para especificar uma versão específica do SDK, aprome-o ao atributo: `Sdk`

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Isso atualmente é a única maneira com suporte para fazer referência a um projeto do SDK no Visual Studio para Mac.

- Use o elemento `<Sdk/>` de nível superior:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Uma importação implícita é adicionada à parte superior e inferior do projeto, como discutido anteriormente.
   
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

Ao avaliar a importação, o MSBuild resolve dinamicamente o caminho para o SDK do projeto com base no nome e na versão especificada.  O MSBuild também tem uma lista de resolvers SDK registrados, que são plug-ins que localizam SDKs de projeto em sua máquina. Os plug-ins incluem:

- Um resolvedor baseado em NuGet que consulta os feeds de pacotes configurados para pacotes do NuGet que correspondem à ID e à versão do SDK que você especificou.

   Este resolver só está ativo se você especificou uma versão opcional. Pode ser usado para qualquer projeto personalizado SDK.
   
- Um resolver .NET CLI que resolve SDKs instalados com [.NET CLI](/dotnet/core/tools/).

   Este resolver localiza sdks `Microsoft.NET.Sdk` `Microsoft.NET.Sdk.Web` do projeto como e que fazem parte do produto.
   
- Um resolvedor padrão que resolve SDKs instalados com o MSBuild.

O resolver SDK baseado em NuGet suporta especificar uma versão no arquivo [global.json,](/dotnet/core/tools/global-json) que permite controlar a versão sdk do projeto em um lugar e não em cada projeto individual:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Somente uma versão de cada SDK de projeto pode ser usada durante uma compilação. Se você referenciar duas versões diferentes do mesmo projeto SDK, o MSBuild emite um aviso. Recomenda-se **não** especificar uma versão em seus projetos se uma versão for especificada no arquivo *global.json.*

## <a name="see-also"></a>Confira também

- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [Personalizar seu build](../msbuild/customize-your-build.md)
- [Pacotes, metadados e estruturas](/dotnet/core/packages)
- [Adições ao formato csproj para .NET Core](/dotnet/core/tools/csproj)
