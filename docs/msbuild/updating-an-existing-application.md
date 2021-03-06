---
title: Atualizar um aplicativo existente para o MSBuild 15 | Microsoft Docs
description: Saiba como garantir que as compilações programáticas de seus aplicativos correspondam às compilações feitas no Visual Studio ou MSBuild.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd7f47466074536c9088840e726f768f62f9346b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965922"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Atualizar um aplicativo existente para o MSBuild 15

Em versões do MSBuild anteriores à 15.0, o MSBuild era carregado do GAC (cache de assembly global) e extensões do MSBuild eram instaladas no registro. Isso garantia que todos os aplicativos usassem a mesma versão do MSBuild e tivessem acesso aos mesmos conjuntos de ferramentas, mas impedia instalações lado a lado de diferentes versões do Visual Studio.

Para dar suporte a uma instalação menor, mais rápida e lado a lado, o Visual Studio 2017 e versões posteriores não colocam mais o MSBuild no GAC nem modificam o registro. Infelizmente, isso significa que aplicativos que desejam usar a API do MSBuild para avaliar ou criar projetos não podem contar implicitamente com a instalação do Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Usar o MSBuild no Visual Studio

Para garantir que builds programáticos de seu aplicativo correspondam àqueles feitos no Visual Studio ou no *MSBuild.exe*, carregue assemblies do MSBuild no Visual Studio e use os SDKs disponíveis dentro do Visual Studio. O pacote NuGet Microsoft.Build.Locator simplifica esse processo.

## <a name="use-microsoftbuildlocator"></a>Usar Microsoft.Build.Locator

Se você redistribuir *Microsoft.Build.Locator.dll* com seu aplicativo, não precisará distribuir outros assemblies do MSBuild.

Atualizar um projeto para usar o MSBuild 15 e a API de localizador requer algumas alterações no seu projeto, descritas abaixo. Para ver um exemplo das alterações necessárias para atualizar um projeto, consulte [As confirmações feitas em um projeto de exemplo no repositório do MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Alterar as referências do MSBuild

Para garantir que o MSBuild seja carregado de um local central, não distribua seus assemblies com seu aplicativo.

O mecanismo para alterar o projeto para evitar carregar o MSBuild de um local central depende de como você faz referência ao MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Usar pacotes NuGet (preferencial)

Essas instruções pressupõem que você esteja usando [referências de NuGet de estilo PackageReference](/nuget/consume-packages/package-references-in-project-files).

Altere os arquivos de projeto para fazer referência a assemblies de MSBuild de seus pacotes NuGet. Especifique `ExcludeAssets=runtime` para informar ao NuGet que os assemblies são necessários somente no momento da compilação, e não devem ser copiados para o diretório de saída.

As versões principal e secundária dos pacotes do MSBuild devem ser menores ou iguais à versão mínima do Visual Studio a que você deseja dar suporte. Por exemplo, se você quiser dar suporte ao Visual Studio 2017 e versões posteriores, faça referência à versão do pacote `15.1.548`.

Por exemplo, você pode usar este XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Usar assemblies de extensão

Se você não puder usar pacotes NuGet, poderá fazer referência aos assemblies do MSBuild distribuídos com o Visual Studio. Se você fizer referência ao MSBuild diretamente, certifique-se de que ele não seja copiado para o diretório de saída por meio da definição de `Copy Local` como `False`. No arquivo de projeto, essa configuração seria semelhante ao seguinte código:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Redirecionamentos de associação

Referencie o pacote Microsoft. Build. Locator para garantir que seu aplicativo use automaticamente os redirecionamentos de associação necessários para a versão 15.1.0.0. Os redirecionamentos de associação para essa versão dão suporte ao MSBuild 15 e ao MSBuild 16.

### <a name="ensure-output-is-clean"></a>Garantir uma saída limpa

Compile o projeto e inspecione o diretório de saída para ter certeza de que ele não contenha assemblies *Microsoft.Build.\*.dll* diferentes de *Microsoft.Build.Locator.dll*, adicionado na próxima etapa.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Adicionar referência de pacote para o Microsoft.Build.Locator

Adicione uma referência de pacote NuGet para o [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Não especifique `ExcludeAssets=runtime` para o pacote do Microsoft.Build.Locator.

### <a name="register-instance-before-calling-msbuild"></a>Registre a instância antes de chamar o MSBuild

> [!IMPORTANT]
> Você não pode fazer referência a nenhum tipo de MSBuild (do `Microsoft.Build` namespace) no método que chama MSBuildLocator. Por exemplo, você não pode fazer isso:
>
> ```csharp
> void ThisWillFail()
> {
>     MSBuildLocator.RegisterDefaults();
>     Project p = new Project(SomePath); // Could be any MSBuild type
>     // Code that uses the MSBuild type
> }
> ```
>
> Em vez disso, você deve fazer isso:
>
> ```csharp
> void MethodThatDoesNotDirectlyCallMSBuild()
> {
>     MSBuildLocator.RegisterDefaults();
>     MethodThatCallsMSBuild();
> }
> 
> void MethodThatCallsMSBuild()
> {
>     Project p = new Project(SomePath);
>     // Code that uses the MSBuild type
> }
> ```

A maneira mais simples de adicionar a chamada à API do localizador é adicionar uma chamada

```csharp
MSBuildLocator.RegisterDefaults();
```

no código de inicialização do aplicativo.

Se quiser ter um controle mais refinado sobre o carregamento do MSBuild, você poderá selecionar um resultado de `MSBuildLocator.QueryVisualStudioInstances()` para passar para `MSBuildLocator.RegisterInstance()` manualmente, mas geralmente isso não é necessário.
