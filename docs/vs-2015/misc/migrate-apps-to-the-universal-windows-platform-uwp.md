---
title: Migrar aplicativos para o Plataforma Universal do Windows (UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5794aa5ab7dc14932c65a9156ea9252e71731155
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299477"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migrar aplicativos para a UWP (Plataforma Universal do Windows)
Faça as alterações manuais necessárias em seus arquivos de projeto existentes para aplicativos da Windows Store 8,1, Windows Phone aplicativos 8,1 ou aplicativos universais do Windows criados com o Visual Studio 2015 RC, para que possam ser usados com o Visual Studio 2015 RTM. (Se você tiver um aplicativo Windows 8.1 universal com um projeto de aplicativo do Windows e Windows Phone projeto, será necessário seguir as etapas para migrar cada projeto.)

 Com o Plataforma Universal do Windows, agora você direciona seu aplicativo para uma ou mais famílias de dispositivos. Se você quiser obter mais informações sobre aplicativos universais do Windows, veja este [Guia de plataforma](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

- [Migre seus aplicativos C#/vb da Windows Store 8,1 ou Windows Phone 8,1 existentes](#MigrateCSharp) para usar o plataforma universal do Windows.

- [Migre seus aplicativos C++ existentes da Windows Store 8,1 ou Windows Phone 8,1](#MigrateCPlusPlus) para usar o plataforma universal do Windows.

- [Alterações necessárias para os aplicativos universais do Windows existentes criados com o Visual Studio 2015 RC](#PreviousVersions).

- [Alterações necessárias para projetos de teste de unidade existentes para aplicativos universais do Windows criados com o Visual Studio 2015 RC](#MigrateUnitTest).

  Se você não quiser fazer todas essas alterações, saiba como [portar seus aplicativos existentes](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) para um novo projeto universal do Windows.

## <a name="MigrateCSharp"></a>Migre seus C#aplicativos do/VB Windows Store 8,1 ou Windows Phone 8,1 para usar o plataforma universal do Windows

#### <a name="migrate-your-cvb-project-files"></a>Migrar C#seus arquivos de projeto do/vb

1. Para localizar o Plataforma Universal do Windows que você instalou, abra esta pasta: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Ele contém uma lista de pastas para cada Plataforma Universal do Windows que está instalado. O nome da pasta é a versão Plataforma Universal do Windows que você instalou. Por exemplo, este dispositivo Windows 10 tem a versão 10.0.10240.0 do Plataforma Universal do Windows instalado.

     ![Abra a pasta para exibir as versões instaladas](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Mais de uma versão do Plataforma Universal do Windows pode ser instalada. Recomendamos que você use a versão mais recente para seu aplicativo.

2. Usando o explorador de arquivos, vá para a pasta na qual seu projeto UWP está armazenado. Crie um arquivo. JSON nessa pasta. Nomeie o arquivo: Project. JSON e, em seguida, adicione o seguinte conteúdo a este arquivo:

    ```json
    {
      "dependencies": {
        "Microsoft.ApplicationInsights": "1.0.0",
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
      },
      "frameworks": {
        "uap10.0": {}
      },
      "runtimes": {
        "win10-arm": {},
        "win10-arm-aot": {},
        "win10-x86": {},
        "win10-x86-aot": {},
        "win10-x64": {},
        "win10-x64-aot": {}
      }
    }

    ```

3. Crie um arquivo chamado Default. Rd. XML com o conteúdo a seguir. Se você tiver um projeto VB, adicione esse arquivo ao diretório meu projeto para o seu projeto. Se você tiver um C# projeto do, adicione esse arquivo ao diretório de propriedades do seu projeto.

    ```xml
    <?xml version="1.0"?>
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->
    <Assembly Dynamic="Required All" Name="*Application*"/>
    <!-- Add your application specific runtime directives here. -->
    </Application></Directives>
    ```

4. Abra sua solução que contém seu aplicativo existente da Windows Store 8,1 ou Windows Phone aplicativo 8,1 no Visual Studio.

5. Clique com o botão direito do mouse no projeto existente para seu aplicativo no Gerenciador de Soluções, em seguida, selecione **descarregar projeto**. Depois que o projeto for descarregado, clique com o botão direito do mouse no arquivo de projeto novamente e escolha Editar o arquivo. csproj ou. vbproj.

     ![Clique com o botão direito do mouse no projeto e escolha Editar](../misc/media/uap-editproject.png "UAP_EditProject")

6. Localize o elemento \<PropertyGroup > que contém o elemento \<> TargetPlatformVersion com um valor de 8,1. Execute as seguintes etapas para este \<elemento de > de PropertyGroup:

    1. Defina o valor do elemento \<da plataforma > como: **x86**.

    2. Adicione um elemento \<TargetPlatformIdentifier > e defina seu valor como: **UAP**.

    3. Altere o valor existente do elemento \<TargetPlatformVersion > para ser o valor da versão Plataforma Universal do Windows que você instalou. Além disso, adicione um elemento \<TargetPlatformMinVersion > e dê a ele o mesmo valor.

    4. Altere o valor do elemento \<MinimumVisualStudioVersion > para: **14**.

    5. Substitua o elemento \<ProjectTypeGuids >, conforme mostrado abaixo:

         Para o C#:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         Para VB:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. Adicione um elemento \<EnableDotNetNativeCompatibleProfile > e defina seu valor como: **true**.

    7. A escala de ativos padrão para aplicativos universais do Windows é 200. Se seu projeto incluir ativos não dimensionados em 200, você precisará adicionar um elemento \<UapDefaultAssetScale > com o valor da escala de seus ativos a esse PropertyGroup. Saiba mais sobre [ativos e escalas](https://msdn.microsoft.com/library/jj679352.aspx).

         Agora, o elemento \<PropertyGroup > deve ser semelhante a este exemplo:

        ```xml
        <PropertyGroup>
            …
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

7. Substitua todas as instâncias de 12,0 por 14,0 para refletir a versão do Visual Studio que você está usando agora. Como essas instâncias:

    ```xml
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

    ```
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">
        <VisualStudioVersion>14.0</VisualStudioVersion>
    ```

8. Localize \<PropertyGroup > elementos configurados para a plataforma AnyCPU como parte do atributo Condition. Remova esses elementos e todos os seus filhos. AnyCPU não tem suporte para aplicativos do Windows 10 no Visual Studio 2015. Por exemplo, você deve remover \<elementos de > PropertyGroup como estes:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
    ```

9. Para cada \<restante > elemento PropertyGroup, verifique se o elemento tem um atributo Condition com uma configuração de versão. Se tiver, mas não contiver um elemento \<UseDotNetNativeToolchain >, em seguida, adicione um. Defina o valor para o elemento \<UseDotNetNativeToolchain > como true, desta forma:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">
        <OutputPath>bin\x64\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <Optimize>true</Optimize>
        <NoWarn>;2008</NoWarn>
        <DebugType>pdbonly</DebugType>
        <PlatformTarget>x64</PlatformTarget>
        <UseVSHostingProcess>false</UseVSHostingProcess>
        <ErrorReport>prompt</ErrorReport>
        <Prefer32Bit>true</Prefer32Bit>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

10. Somente para projetos Windows Phone, remova o elemento \<PropertyGroup > que contém um elemento \<TargetPlatformIdentifier > com um valor de WindowsPhoneApp. Remova também todos os filhos deste elemento:

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. Localize o elemento \<rowgroup > que contém o elemento \<AppxManifest >. Adicione o seguinte \<nenhum elemento > como um filho do elemento \<rowgroup >:

    ```xml
    <None Include="project.json" />
    ```

12. Localize o elemento \<rowgroup > que contém outros ativos que são adicionados ao seu projeto, como arquivos de logotipo. png (\<conteúdo include = "Assets\Logo.scale-100.png"/>). Adicione o seguinte conteúdo de \<> elemento filho a este \<elemento > do grupo de itens:

     **Para C#:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **Para VB:**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. Localize o elemento \<rowgroup > que inclui \<referência > elementos filhos aos pacotes NuGet. Anote os pacotes NuGet que você usa, pois você precisará baixá-los com o Gerenciador de pacotes NuGet depois que seu projeto for recarregado. Remova esse \<> do rowgroup junto com seus filhos. Por exemplo, um projeto UWP poderia ter os seguintes pacotes NuGet que precisam ser removidos:

    ```xml
    <ItemGroup>
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
          <Private>True</Private>
        </Reference>
      </ItemGroup>
    ```

14. Salve as alterações.

15. Feche o arquivo. csproj ou. vbproj.

16. Clique com o botão direito do mouse em seu projeto no Gerenciador de Soluções e escolha recarregar projeto no menu de contexto. Todos os arquivos em seu projeto agora devem ser exibidos no Gerenciador de Soluções.

17. Use o Gerenciador do NuGet para adicionar novamente os pacotes que você excluiu em uma etapa anterior.

     Agora você precisa seguir as etapas para [atualizar os arquivos de manifesto do pacote](#PackageManifest) para todos os seus projetos da Windows Store 8,1 ou Windows Phone 8,1.

## <a name="MigrateCPlusPlus"></a>Migre seus C++ aplicativos da Windows Store 8,1 ou Windows Phone 8,1 para usar o plataforma universal do Windows

#### <a name="migrate-your-c-project-files"></a>Migrar C++ seus arquivos de projeto

1. Para localizar o Plataforma Universal do Windows que você instalou, abra esta pasta: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Ele contém uma lista de pastas para cada Plataforma Universal do Windows que está instalado. O nome da pasta é a versão Plataforma Universal do Windows que você instalou. Por exemplo, este dispositivo Windows 10 tem a versão 10.0.10240.0 do Plataforma Universal do Windows instalado.

     ![Abra a pasta para exibir as versões instaladas](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Mais de uma versão do Plataforma Universal do Windows pode ser instalada. Recomendamos que você use a versão mais recente para seu aplicativo.

2. Abra sua solução que contém seu aplicativo C++ existente da Windows Store 8,1 ou Windows Phone aplicativo 8,1 no Visual Studio.

     Clique com o botão direito do mouse no projeto existente no Gerenciador de soluções e selecione **descarregar projeto**. Depois que o projeto for descarregado, clique com o botão direito do mouse no arquivo de projeto novamente e escolha Editar o arquivo. vcxproj.

     ![Clique&#45;com o botão direito do mouse em arquivo de projeto e escolha Editar](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. Localize o elemento \<PropertyGroup > que contém o elemento \<> ApplicationTypeRevision com um valor de 8,1. Execute as seguintes etapas para este \<elemento de > de PropertyGroup:

    1. Adicione um elemento \<WindowsTargetPlatformVersion > e um \<elemento > WindowsTargetPlatformMinVersion e dê a eles o valor da versão Plataforma Universal do Windows que você instalou.

    2. Atualize o valor do elemento ApplicationTypeRevision de 8,1 para 10,0.

    3. Altere o valor do elemento \<MinimumVisualStudioVersion > para: 14.

    4. Adicione um elemento \<EnableDotNetNativeCompatibleProfile > e defina seu valor como: true.

    5. A escala de ativos padrão para aplicativos universais do Windows é 200. Se seu projeto incluir ativos não dimensionados em 200, você precisará adicionar um elemento \<UapDefaultAssetScale > com o valor da escala de seus ativos a esse PropertyGroup. Saiba mais sobre [ativos e escalas](https://msdn.microsoft.com/library/jj679352.aspx).

    6. Somente para projetos de Windows Phone, altere o valor de \<> de aplicativo de Windows Phone para a Windows Store.

         Agora, o elemento \<PropertyGroup > deve ser semelhante a este exemplo:

        ```xml
        <PropertyGroup>
            …
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
             <ApplicationType>Windows Store</ApplicationType>
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

4. Altere todas as instâncias do elemento \<PlatformToolset > para que o valor v140. Por exemplo:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. Para cada \<restante > elemento PropertyGroup, verifique se o elemento tem um atributo Condition com uma configuração de versão. Se tiver, mas não contiver um elemento \<UseDotNetNativeToolchain >, em seguida, adicione um. Defina o valor para o elemento \<UseDotNetNativeToolchain > como true, desta forma:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

6. Salve as alterações. Em seguida, feche o arquivo de projeto.

7. Clique com o botão direito do mouse no arquivo de projeto em Gerenciador de Soluções e escolha recarregar projeto no menu de contexto. Todos os arquivos em seu projeto agora devem ser exibidos no Gerenciador de Soluções.

     Agora você precisa seguir as etapas para [atualizar os arquivos de manifesto do pacote](#PackageManifest) para todos os seus projetos da Windows Store 8,1 ou Windows Phone 8,1.

## <a name="PackageManifest"></a>Atualize o arquivo de manifesto do pacote para todos os seus projetos da Windows Store 8,1 ou Windows Phone 8,1
 Você deve atualizar o arquivo de manifesto do pacote para cada projeto em sua solução.

#### <a name="update-your-package-manifest-file"></a>Atualizar o arquivo de manifesto do pacote

1. Abra o arquivo Package. appxmanifest em seu projeto. Você precisa editar o arquivo Package. AppxManifest para cada um dos seus projetos da Windows Store e Windows Phone.

2. Você precisa atualizar o elemento de > do pacote de \<com os novos esquemas com base em seu tipo de projeto existente. Primeiro, remova os esquemas abaixo com base em se você tem uma Windows Store ou Windows Phone projeto.

    **Antigo para o projeto da Windows Store:** O elemento > do pacote de \<será semelhante a este.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **Antigo para Windows Phone projeto:** O elemento > do pacote de \<será semelhante a este.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **Novo para plataforma universal do Windows:** Adicione os esquemas abaixo ao seu \<pacote > elemento. Remova qualquer prefixo de identificador de namespace associado dos elementos para os esquemas que você acabou de remover. Atualize a propriedade IgnorableNamespaces para: UAP MP. Seu novo pacote de \<de > elemento deve ser semelhante a este.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. Adicione uma dependência de \<> elemento filho ao elemento de > do pacote de \<. Em seguida, adicione um elemento filho \<TargetDeviceFamily > a este \<dependências > elemento com os atributos Name, MinVersion e MaxVersionTested. Dê ao atributo Name o valor: Windows. universal. Dê a MinVersion e MaxVersionTested o valor da versão Plataforma Universal do Windows que você instalou. Esse elemento deve ser semelhante a este:

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **Somente para Windows Store:** Você precisa adicionar um elemento filho \<MP: PhoneIdentity > ao elemento > do pacote de \<. Adicione um atributo PhoneProductId e um atributo PhonePublisherId. Defina PhoneProductId para ter o mesmo valor que o atributo Name no elemento \<Identity >. Defina o valor de PhonePublishedId como: 00000000-0000-0000-0000-000000000000. Assim:

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. Localize o elemento \<pré-requisitos > e exclua esse elemento e quaisquer elementos filho que ele tenha.

6. Adicione o namespace **UAP** ao seguinte \<recurso > elementos: Scale, DXFeatureLevel. Por exemplo:

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. Adicione o namespace **UAP** ao seguinte \<funcionalidade > elementos: DocumentsLibrary, PicturesLibrary, VideosLibrary, MusicLibrary, EnterpriseAuthentication, SharedUserCertificates, removableStorage, compromissos e contatos. Por exemplo:

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. Adicione o namespace **UAP** ao elemento \<VisualElements > e a qualquer um de seus elementos filho. Por exemplo:

   ```xml
   <uap:VisualElements
       DisplayName="My WWA App"
       Square150x150Logo="images/150x150.png"
       Square44x44Logo="images/44x44.png"
       Description="My WWA App"
       BackgroundColor="#777777">
     <uap:SplashScreen Image="images/splash.png"/>
   </uap:VisualElements>

   ```

    **Aplica-se somente à Windows Store:** Os nomes de tamanho do bloco foram alterados. Altere os atributos no elemento \<VisualElements > para refletir os novos tamanhos de bloco convergidos. 70x70 se torna 71 x 71 e 30x30 se torna 44x44.

    **Antigo:** nomes de tamanho de bloco

   ```xml
   <m2:VisualElements
       …
       Square30x30Logo="Assets\SmallLogo.png"
       …>
    <m2:DefaultTile
         …
         Square70x70Logo="images/70x70.png">
   </m2:VisualElements>

   ```

    **Novo:** nomes de tamanho de bloco

   ```xml
   <uap:VisualElements
       …
       Square44x44Logo="Assets\SmallLogo.png"
       …>
    <uap:DefaultTile
         …
         Square71x71Logo="images/70x70.png">
   </uap:VisualElements>

   ```

9. Adicione o namespace **UAP** ao \<ApplicationContentUriRules > e a todos os seus elementos filho. Por exemplo:

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. Adicione o namespace **UAP** à seguinte extensão de \<> elementos e todos os seus elementos filho: Windows. accountPictureProvide, Windows. Alarm, Windows. appointmentsProvider Windows. autoPlayContent, Windows. autoPlayDevice, Windows. cachedFileUpdate, Windows. cameraSettings, Windows. fileOpenPicker, Windows. fileTypeAssociation, Windows. fileSavePicke, Windows. lockScreenCall, Windows. printTaskSettings, Windows. Protocol, Windows. Search, Windows. shareTarget. Por exemplo:

    ```xml
    <Extensions>
      <uap:Extension Category="windows.alarm"/>
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>
      <uap:Extension Category="windows.protocol">
        <uap:Protocol Name="mailto" DesiredView="useHalf">
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>
        </uap:Protocol>
      </uap:Extension>
    </Extensions>

    ```

11. Adicione o namespace **UAP** a tarefas em segundo plano do tipo chatMessageNotification. Por exemplo:

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
     <BackgroundTasks ServerName="MyBackgroundTasks">
        <uap:Task Type="chatMessageNotification"/>
      </BackgroundTasks>
    </Extension>

    ```

12. Altere as dependências de estrutura. Adicione um nome de editor a todos os elementos \<PackageDependency > e especifique um MinVersion se ele ainda não estiver especificado.

     **Antigo:** \<PackageDependency > elemento

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **Novo:** \<elemento de > PackageDependency

    ```xml
    <Dependencies>
     <PackageDependency
          Name="Microsoft.VCLibs.120.00"
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
          MinVersion="12.0.30113.0" />
    </Dependencies>

    ```

     Use os valores apropriados de editor e MinVersion para a estrutura real que você está usando. Lembre-se de que esses nomes podem mudar para o Windows 10.

13. Substitua as tarefas de tipo de plano de fundo gattCharacteristicNotification e rfcommConnection por uma tarefa de tipo Bluetooth. Por exemplo:

     **ANTIGO**

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
                <Task Type="rfcommConnection"/>
               <Task Type="gattCharacteristicNotification"/>
    </BackgroundTasks>
    </Extension>
    ```

     **Novo:** Com a tarefa de tipo de Bluetooth.

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
               <Task Type="bluetooth"/>
    </BackgroundTasks>
    </Extension>
    ```

14. Substitua os recursos de dispositivo Bluetooth Bluetooth. RFCOMM e Bluetooth. genericAttributeProfile por um recurso Bluetooth genérico. Por exemplo:

     **ANTIGO**

    ```xml
    <Capabilities>
      <m2:DeviceCapability Name="bluetooth.rfcomm">
        <m2:Device Id="any">
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>
        </m2:Device>
      </m2:DeviceCapability>
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">
        <m2:Device Id="any">
         <m2:Function Type="name:heartRate"/>
        </m2:Device>
      </m2:DeviceCapability>
    </Capabilities>
    ```

     **Novo:** Substituído por um recurso Bluetooth genérico.

    ```xml
    <Capabilities>
      <uap:DeviceCapability Name="bluetooth"/>
    </Capabilities>

    ```

15. Remova todos os elementos preteridos.

    1. Estes atributos para \<VisualElements > foram preteridos e devem ser removidos:

       - O \<VisualElements > atributos: ForegroundText, ToastCapable

       - O atributo de \<defaulttile > DefaultSize

       - O elemento \<ApplicationView >

         Por exemplo:

       ```xml
       <m2:VisualElements
           …
           ForegroundText="dark"
           ToastCapable="true">
       <m2:DefaultTile DefaultSize="square150x150Logo"/>
         <m2:ApplicationView MinWidth="width320"/>
       </m2:VisualElements>

       ```

    2. Remova as extensões Windows. Contact e Windows. contactPicker e todos os elementos nessas extensões.

16. Salve o arquivo Package. appxmanifest. Em seguida, feche o Visual Studio.

17. Você precisa remover alguns arquivos ocultos antes de poder reabrir a solução.

    1. Abra o explorador de arquivos, clique em **Exibir** na barra de ferramentas e selecione **itens ocultos** e **extensões de nome de arquivo**. Abra esta pasta em seu computador: \<caminho para o local da sua solução >\\. vs\\{nome do projeto} \v14. Se houver um arquivo com uma extensão de arquivo. suo, exclua-o.

    2. Agora, volte para a pasta onde a solução está localizada. Abra todas as pastas para projetos que existem em sua solução. Se um arquivo dentro de qualquer uma dessas pastas de projeto tiver uma extensão. csproj. User ou. vbproj. User, exclua-a.

         Agora você pode reabrir sua solução no Visual Studio. Você está pronto para codificar, criar e depurar seu aplicativo usando o Plataforma Universal do Windows.

         Saiba como [adaptar seu código](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) para aproveitar as novidades do plataforma universal do Windows.

## <a name="PreviousVersions"></a>Alterações necessárias para os aplicativos universais do Windows criados com o Visual Studio 2015 RC
 Se você criou aplicativos universais do Windows 10 com o Visual Studio 2015 RC, você precisa redirecionar seu projeto para usar a versão do Plataforma Universal do Windows instalada com a versão mais recente do Visual Studio 2015. Não há suporte para nenhuma versão anterior. As alterações necessárias são diferentes dependendo do idioma usado para criar seu aplicativo:

- [C#Aplicativos/VB](#RCUpdate10CSharp)

- [C++os](#RCUpdate10CPlusPlus)

### <a name="RCUpdate10CSharp"></a>Atualize seus C#projetos do/vb para usar as plataforma universal do Windows mais recentes
 Quando você abrir sua solução para seu aplicativo existente, verá que seu aplicativo requer uma atualização:

 ![Exibir seu projeto no Gerenciador de Soluções](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 Se você optar por recarregar este projeto de Gerenciador de Soluções, verá esta caixa de diálogo:

 ![Redirecione seu aplicativo para usar o SDK correto](../misc/media/missingsdkforuap.png "MissingSDKforUAP")

 Como o SDK do Plataforma Universal do Windows para seu projeto agora não tem suporte, você não poderá instalá-lo. Basta clicar em OK e, em seguida, seguir as etapas abaixo.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Atualize seus C#projetos do/vb para usar as plataforma universal do Windows mais recentes

1. Para localizar o Plataforma Universal do Windows que você instalou, abra esta pasta: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Ele contém uma lista de pastas para cada Plataforma Universal do Windows que está instalado. O nome da pasta é a versão Plataforma Universal do Windows que você instalou. Por exemplo, este dispositivo Windows 10 tem a versão 10.0.10240.0 do Plataforma Universal do Windows instalado.

    ![Abra a pasta para exibir as versões instaladas](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

    Mais de uma versão do Plataforma Universal do Windows pode ser instalada. Recomendamos que você use a versão mais recente para seu aplicativo.

2. Usando o explorador de arquivos, vá para a pasta na qual seu projeto UWP está armazenado. Exclua o arquivo Packages. config e crie um novo arquivo. JSON nessa pasta. Nomeie o arquivo: Project. JSON e, em seguida, adicione o seguinte conteúdo a este arquivo:

   ```json

   {
     "dependencies": {
       "Microsoft.ApplicationInsights": "1.0.0",
       "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
       "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
       "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
     },
     "frameworks": {
       "uap10.0": {}
     },
     "runtimes": {
       "win10-arm": {},
       "win10-arm-aot": {},
       "win10-x86": {},
       "win10-x86-aot": {},
       "win10-x64": {},
       "win10-x64-aot": {}
     }
   }

   ```

3. Com o Visual Studio, abra sua solução que contém C#seu aplicativo/VB universal do Windows. Você verá que o arquivo de projeto (. csproj ou. vbproj) precisa ser atualizado. Clique com o botão direito do mouse no arquivo de projeto e escolha Editar este arquivo.

    ![Clique com o botão direito do mouse no projeto e escolha Editar](../misc/media/uap-editproject.png "UAP_EditProject")

4. Localize o elemento \<PropertyGroup > que contém os elementos \<> TargetPlatformVersion e \<TargetPlatformMinVersion >. Altere o valor existente do \<TargetPlatformVersion > e \<elementos de > de TargetPlatformMinVersion para a mesma versão do Plataforma Universal do Windows que você instalou.

    A escala de ativos padrão para aplicativos universais do Windows é 200. Projetos criados com os ativos do Visual Studio 2015 RC incluídos dimensionados em 100, você precisará adicionar um elemento \<UapDefaultAssetScale > com um valor de 100 a esse PropertyGroup. Saiba mais sobre [ativos e escalas](https://msdn.microsoft.com/library/jj679352.aspx).

5. Se você adicionou quaisquer referências aos SDKs de extensão UWP (por exemplo: o SDK do Windows Mobile), será necessário atualizar a versão do SDK. Por exemplo, este \<elemento de > SDKReference:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

    Deve ser alterado para:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

6. Localize o elemento de > de destino \<com um atributo de nome que tenha o valor: EnsureNuGetPackageBuildImports. Exclua este elemento e todos os seus filhos.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. Localize e exclua os elementos de importação de > de \<com atributos de projeto e condição que referenciam Microsoft. Diagnostics. Tracing. EventSource e Microsoft. ApplicationInsights, da seguinte maneira:

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. Localize o > \<rowgroup que tem \<referência > elementos filhos aos pacotes NuGet. Anote os pacotes NuGet que são referenciados, pois você precisará dessas informações para uma etapa futura. Uma diferença significativa entre o formato de projeto do Windows 10 entre o Visual Studio 2015 RC e o Visual Studio 2015 RTM é que o formato RTM usa o [NuGet](https://docs.microsoft.com/nuget/) versão 3.

    Remova o > \<rowgroup e todos os seus filhos. Por exemplo, um projeto UWP criado com o Visual Studio RC terá os seguintes pacotes NuGet que precisam ser removidos:

   ```xml
   <ItemGroup>
       <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
         <Private>True</Private>
       </Reference>
     </ItemGroup>

   ```

9. Localize o elemento \<rowgroup > que contém um elemento \<AppxManifest >. Se houver um \<nenhum elemento > com um atributo Include definido como: packages. config, exclua-o. Além disso, adicione uma \<nenhum elemento > com um atributo Include e defina seu valor como: Project. JSON.

10. Salve as alterações. Em seguida, feche o arquivo de projeto.

11. Clique com o botão direito do mouse no arquivo de projeto em Gerenciador de Soluções e escolha recarregar projeto no menu de contexto. Todos os arquivos em seu projeto agora devem ser exibidos no Gerenciador de Soluções.

12. Selecione o arquivo ApplicationInsights. config em Gerenciador de Soluções e abra suas propriedades. Defina a propriedade ação de compilação como "conteúdo" e a propriedade copiar para o diretório de saída como "copiar se for mais recente".

13. Abra o arquivo Package. appxmanifest em seu projeto.

    1. Localize o elemento \<TargetDeviceFamily >. Altere seus atributos MinVersion e MaxVersionTested para corresponder à versão de Plataforma Universal do Windows que você instalou. Assim:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Salve as alterações.

14. Use o Gerenciador do NuGet para adicionar os pacotes que você excluiu na etapa anterior. Uma diferença significativa entre o formato de projeto do Windows 10 entre o Visual Studio 2015 RC e o Visual Studio 2015 RTM é que o formato RTM usa o [NuGet](https://docs.microsoft.com/nuget/) versão 3.

    Agora você pode codificar, criar e depurar seu aplicativo.

    Se você tiver projetos de teste de unidade para seus aplicativos universais do Windows, também deverá seguir [estas etapas](#MigrateUnitTest).

### <a name="RCUpdate10CPlusPlus"></a>Atualize seus C++ projetos para usar as plataforma universal do Windows mais recentes

1. Para localizar o Plataforma Universal do Windows que você instalou, abra esta pasta: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Ele contém uma lista de pastas para cada Plataforma Universal do Windows que está instalado. O nome da pasta é a versão Plataforma Universal do Windows que você instalou. Por exemplo, este dispositivo Windows 10 tem a versão 10.0.10240.0 do Plataforma Universal do Windows instalado.

     ![Abra a pasta para exibir as versões instaladas](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Mais de uma versão do Plataforma Universal do Windows pode ser instalada. Recomendamos que você use a versão mais recente para seu aplicativo.

2. Abra sua solução que contém seu C++ aplicativo universal do Windows. Clique com o botão direito do mouse no arquivo Project. vcxproj e escolha descarregar o arquivo de projeto. Depois que o projeto for descarregado, clique com o botão direito do mouse no arquivo de projeto novamente e escolha editá-lo.

     ![Descarregue o projeto e edite o arquivo de projeto](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. Encontre qualquer \<PropertyGroup > elementos que não contenham um atributo Condition, mas que contenham um elemento \<> ApplicationTypeRevision. Atualize o valor de ApplicationTypeRevision de 8,2 para 10,0. Adicione um \<WindowsTargetPlatformVersion > e um \<elemento > WindowsTargetPlatformMinVersion e defina seus valores como o valor da versão Plataforma Universal do Windows que você instalou.

     Adicione um elemento \<EnableDotNetNativeCompatibleProfile > e defina seu valor como true se o elemento ainda não existir.

     A escala de ativos padrão para aplicativos universais do Windows é 200. Projetos criados com os ativos do Visual Studio 2015 RC incluídos dimensionados em 100, você precisará adicionar um elemento \<UapDefaultAssetScale > com um valor de 100 a esse PropertyGroup. Saiba mais sobre [ativos e escalas](https://msdn.microsoft.com/library/jj679352.aspx).

     Portanto, isso \<elemento de > PropertyGroup agora será semelhante a este:

    ```xml
    <PropertyGroup Label="Globals">
        …
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>
        <ApplicationType>Windows Store</ApplicationType>
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
        <UapDefaultAssetScale>100</UapDefaultAssetScale>
      </PropertyGroup>

    ```

4. Para cada \<restante > elemento PropertyGroup, verifique se o elemento tem um atributo Condition com uma configuração de versão. Se tiver, mas não contiver um elemento \<UseDotNetNativeToolchain >, em seguida, adicione um. Defina o valor para o elemento \<UseDotNetNativeToolchain > como true, desta forma:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. Você precisa atualizar o elemento \<EnableDotNetNativeCompatibleProfile > e o elemento \<> do UseDotNetNativeToolchain para habilitar o .NET Native, mas o .NET Native não está habilitado C++ nos modelos.

     Salve as alterações. Em seguida, feche o arquivo de projeto.

6. Clique com o botão direito do mouse no arquivo de projeto em Gerenciador de Soluções e escolha recarregar projeto no menu de contexto. Todos os arquivos em seu projeto agora devem ser exibidos no Gerenciador de Soluções.

7. Abra o arquivo Package. appxmanifest em seu projeto.

    1. Localize o elemento \<TargetDeviceFamily >. Altere seus atributos MinVersion e MaxVersionTested para corresponder à versão de Plataforma Universal do Windows que você instalou. Assim:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Salve as alterações.

         Agora você pode codificar, criar e depurar seu aplicativo.

         Se você tiver projetos de teste de unidade para seus aplicativos universais do Windows, também deverá seguir [estas etapas](#MigrateUnitTest).

## <a name="MigrateUnitTest"></a>Alterações necessárias para projetos de teste de unidade existentes para aplicativos universais do Windows criados com o Visual Studio 2015 RC
 Se você criou projetos de teste de unidade para aplicativos universais do Windows 10 com o Visual Studio 2015 RC, precisará fazer essas alterações adicionais em seus arquivos de projeto para usar esses projetos de teste com a versão mais recente do Visual Studio 2015. As alterações necessárias são diferentes dependendo do idioma usado para criar seu aplicativo:

- [C#Aplicativos/VB](#UnitTestRCUpdate10CSharp)

- [C++os](#UnitTestRCUpdate10CPlusPlus)

### <a name="UnitTestRCUpdate10CSharp"></a>Atualizar seus C#projetos de teste de unidade do/vb

1. Com o Visual Studio, abra sua solução que contém C#o projeto de teste de unidade do/VB. Altere o valor do elemento \<OuttputType > para: AppContainerExe.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Substitua esse elemento \<EnableCoreRuntime > false\</EnableCoreRuntime > pelo seguinte elemento:

   ```xml

   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>

   ```

3. Remova as seguintes linhas:

   ```xml

   <PropertyGroup>
       <AppXPackage>True</AppXPackage>
       <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
       <PlatformTarget>AnyCPU</PlatformTarget>
       <DebugType>pdbonly</DebugType>
       <Optimize>true</Optimize>
       <OutputPath>bin\Release\</OutputPath>
       <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
       <ErrorReport>prompt</ErrorReport>
       <WarningLevel>4</WarningLevel>
    </PropertyGroup>

   ```

4. Adicione este elemento \<UseDotNetNativeToolchain > true\</UseDotNetNativeToolchain > como um elemento filho a esses grupos de propriedades:

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Exclua os seguintes \<elementos > do grupo de itens:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="packages.config" />
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\Default.rd.xml" />
      <Content Include="Assets\Logo.scale-240.png" />
      <Content Include="Assets\SmallLogo.scale-240.png" />
      <Content Include="Assets\SplashScreen.scale-240.png" />
      <Content Include="Assets\Square71x71Logo.scale-240.png" />
      <Content Include="Assets\StoreLogo.scale-240.png" />
      <Content Include="Assets\WideLogo.scale-240.png" />
   </ItemGroup>

   ```

    Substitua-os por estes elementos:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTestApp.xaml.cs">
         <DependentUpon>UnitTestApp.xaml</DependentUpon>
      </Compile>
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <ApplicationDefinition Include="UnitTestApp.xaml">
         <Generator>MSBuild:Compile</Generator>
         <SubType>Designer</SubType>
      </ApplicationDefinition>
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\UnitTestApp.rd.xml" />
      <Content Include="Assets\LockScreenLogo.scale-200.png" />
      <Content Include="Assets\SplashScreen.scale-200.png" />
      <Content Include="Assets\Square150x150Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
      <Content Include="Assets\StoreLogo.png" />
      <Content Include="Assets\Wide310x150Logo.scale-200.png" />
   </ItemGroup>
   ```

6. Crie um novo projeto de teste de unidade e copie os arquivos UnitTestApp. XAML e UnitTestApp.xaml.cs desse novo projeto para o projeto de teste de unidade existente que você está atualizando.

7. Copie o arquivo UnitTestApp. Rd. XML da pasta propriedades do novo projeto de teste de unidade para a pasta propriedades do projeto de teste de unidade existente que você está atualizando.

8. Abra o arquivo Package. appxmanifest em seu projeto. Em seguida, exclua estes elementos:

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="vstest.executionengine.appcontainer.uap.exe"
            EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
         <uap:VisualElements
            DisplayName="UnitTestProject1"
            Square150x150Logo="Assets\Logo.png"
            Square44x44Logo="Assets\SmallLogo.png"
            Description="UnitTestProject1"
            BackgroundColor="#464646">
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClientServer" />
   </Capabilities>
   ```

    Substitua esses elementos excluídos pelos elementos a seguir. Use o valor apropriado para ProjectName com base no nome do seu projeto, em vez de UnitTestProject1 nos elementos abaixo:

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="$targetnametoken$.exe"
            EntryPoint="UnitTestProject1.App">
         <uap:VisualElements
               DisplayName="UnitTestProject1"
               Square150x150Logo="Assets\Square150x150Logo.png"
               Square44x44Logo="Assets\Square44x44Logo.png"
               Description="UnitTestProject1"
               BackgroundColor="transparent">
            <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClient" />
   </Capabilities>
   ```

   Agora você pode executar os testes de unidade.

### <a name="UnitTestRCUpdate10CPlusPlus"></a>Atualize seus C++ projetos para usar as plataforma universal do Windows mais recentes

1. Com o Visual Studio, abra sua solução que contém C++ o projeto de teste de unidade. Remova os seguintes elementos:

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Adicione os seguintes \<ProjectConfiguration > elementos abaixo deste elemento \<rowgroup Label = "ProjectConfigurations" > se eles ainda não estiverem neste Fille:

    ```xml

    <ProjectConfiguration Include="Debug|x64">
       <Configuration>Debug</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|x64">
       <Configuration>Release</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>

    ```

3. Substituir todas as ocorrências deste elemento:

    ```xml

    <ConfigurationType>DynamicLibrary</ConfigurationType>

    ```

     Com isso:

    ```xml

    <ConfigurationType>Application</ConfigurationType>

    ```

4. Adicione esses \<elementos do PropertyGroup > se eles ainda não estiverem no arquivo:

    ```xml

    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>true</UseDebugLibraries>
       <PlatformToolset>v140</PlatformToolset>
    </PropertyGroup>
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>false</UseDebugLibraries>
       <WholeProgramOptimization>true</WholeProgramOptimization>
       <PlatformToolset>v140</PlatformToolset>
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
    </PropertyGroup>

    ```

5. Substituir todas as ocorrências deste elemento:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
    ```

     Com isso:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>

    ```

6. Substituir todas as ocorrências deste elemento:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

     Com isso:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

7. Adicione esses \<elementos de > ItemDefinitionGroup na seção que já contém outros elementos de > do ItemDefinitionGroup \<:

    ```xml

    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
    <Link>
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
    </Link>
    </ItemDefinitionGroup>
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
       <Link>
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
       </Link>
    </ItemDefinitionGroup>

    ```

8. Exclua o seguinte \< elemento > do grupo de itens:

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Substitua-o por este \<elemento > do rowgroup:

    ```xml

    <ItemGroup>
       <Image Include="Assets\LockScreenLogo.scale-200.png" />
       <Image Include="Assets\SplashScreen.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
       <Image Include="Assets\Square150x150Logo.scale-200.png" />
       <Image Include="Assets\StoreLogo.png" />
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />
    </ItemGroup>

    ```

9. Exclua o seguinte \< elemento > do grupo de itens:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Substitua-o por estes \<elementos de > do rowgroup:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
       <ClInclude Include="UnitTestApp.xaml.h">
          <DependentUpon>UnitTestApp.xaml</DependentUpon>
       </ClInclude>
    </ItemGroup>
    <ItemGroup>
       <ApplicationDefinition Include="UnitTestApp.xaml">
          <SubType>Designer</SubType>
       </ApplicationDefinition>
    </ItemGroup>

    ```

10. Exclua o seguinte elemento:

    ```xml
    <ClCompile Include="UnitTest.cpp"/>
    ```

     Substitua-o por estes \<elementos de > de CICompile:

    ```xml

    <ClCompile Include="UnitTestApp.xaml.cpp">
       <DependentUpon>UnitTestApp.xaml</DependentUpon>
    </ClCompile>
    <ClCompile Include="UnitTest.cpp"/>

    ```

11. Adicione este elemento:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
    ```

     Acima desse elemento no arquivo:

    ```xml

    <ItemGroup>
       <Xml Include="UnitTestApp.rd.xml" />
    </ItemGroup>
    ```

12. Crie um novo projeto de C++ teste de unidade e copie os arquivos UnitTestApp. XAML, UnitTestApp. XAML. cpp, UnitTestApp. XAML. h e UnitTestApp. Rd. XML desse projeto para o projeto existente que você está atualizando.

13. Abra o arquivo Package. appxmanifest em seu projeto. Em seguida, exclua estes elementos:

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
             Executable="vstest.executionengine.appcontainer.uap.exe"
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
          <uap:VisualElements
             DisplayName="UnitTestProject1"
             Square150x150Logo="Assets\Logo.png"
             Square44x44Logo="Assets\SmallLogo.png"
             Description="UnitTestProject1"
             BackgroundColor="#464646">
             <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClientServer" />
    </Capabilities>

    ```

     Substitua esses elementos excluídos pelos elementos a seguir. Use o valor apropriado para ProjectName com base no nome do seu projeto, em vez de UnitTestProject1 nos elementos abaixo:

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
                Executable="$targetnametoken$.exe"
                EntryPoint="UnitTestProject1.App">
          <uap:VisualElements
                DisplayName="UnitTestProject1"
                Square150x150Logo="Assets\Square150x150Logo.png"
                Square44x44Logo="Assets\Square44x44Logo.png"
                Description="UnitTestProject1"
                BackgroundColor="transparent">
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
                <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClient" />
    </Capabilities>

    ```