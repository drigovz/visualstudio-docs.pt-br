---
title: Suporte para propriedades de projeto e configuração | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b03bc04b1d5b87219110aa65bee53c4a4a8f77e2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301063"
---
# <a name="support-for-project-and-configuration-properties"></a>Suporte para propriedades do projeto e de configuração
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A janela **Propriedades** na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE) pode exibir o projeto e as propriedades de configuração. Você pode fornecer uma página de propriedades para seu próprio tipo de projeto para que o usuário possa definir propriedades para seu aplicativo.  
  
 Ao selecionar um nó de projeto no **Gerenciador de soluções** e, em seguida, clicar em **Propriedades** no menu **projeto** , você pode abrir uma caixa de diálogo que inclui propriedades de projeto e configuração. Em [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]e tipos de projeto derivados desses idiomas, essa caixa de diálogo aparece como uma página com guias na [caixa de diálogo geral, ambiente, opções](../../ide/reference/general-environment-options-dialog-box.md). Para obter mais informações, veja como [não está no Build: Walkthrough: expondo o projetoC#e as propriedades de configuração ()](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 A estrutura de pacote gerenciada para projetos (MPFProj) fornece classes auxiliares para criar e gerenciar o novo sistema de projeto. Você pode encontrar o código-fonte e as instruções de compilação em [MPF for projects-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistência do projeto e das propriedades de configuração  
 As propriedades de projeto e configuração são mantidas em um arquivo de projeto que tem uma extensão de nome de arquivo associada ao tipo de projeto, por exemplo,. csproj,. vbproj e. MyProj. Os projetos de linguagem normalmente usam um arquivo de modelo para gerar o arquivo de projeto. No entanto, há, na verdade, várias maneiras de associar modelos e tipos de projeto. Para obter mais informações, consulte [NIB: modelos do Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) e [Descrição do diretório do modelo (. VSDir) arquivos](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 As propriedades Project e Configuration são criadas adicionando itens ao arquivo de modelo. Essas propriedades ficam disponíveis para qualquer projeto criado usando o tipo de projeto que usa esse modelo. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projetos e os MPFProj usam o esquema de [visão geral não está em compilação: MSBuild](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) para arquivos de modelo. Esses arquivos têm uma seção PropertyGroup para cada configuração. As propriedades de projetos normalmente são mantidas na primeira seção PropertyGroup, que tem um argumento de configuração definido como uma cadeia de caracteres nula.  
  
 O código a seguir mostra o início de um arquivo de projeto do MSBuild básico.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 Neste arquivo de projeto, `<Name>` e `<SchemaVersion>` são propriedades do projeto e `<Optimize>` é uma propriedade de configuração.  
  
 É responsabilidade do projeto persistir o projeto e as propriedades de configuração do arquivo de projeto.  
  
> [!NOTE]
> Um projeto pode otimizar a persistência mantendo apenas valores de propriedade que diferem de seus valores padrão.  
  
## <a name="support-for-project-and-configuration-properties"></a>Suporte para propriedades do projeto e de configuração  
 A classe `Microsoft.VisualStudio.Package.SettingsPage` implementa as páginas de propriedades de projeto e de configuração. A implementação padrão de `SettingsPage` oferece propriedades públicas para um usuário em uma grade de propriedade genérica. O método `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` seleciona classes derivadas de `SettingsPage` para grades de propriedades de projeto. O método `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` seleciona classes derivadas de `SettingsPage` para grades de propriedades de configuração. O tipo de projeto deve substituir esses métodos para selecionar as páginas de propriedades apropriadas.  
  
 A classe `SettingsPage` e a classe `Microsoft.VisualStudio.Package.ProjectNode` oferecem esses métodos para persistir as propriedades de projeto e configuração:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` Propriedades do projeto de persistência.  
  
- as propriedades de configuração `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` Persist.  
  
  > [!NOTE]
  > As implementações das classes `Microsoft.VisualStudio.Package.SettingsPage` e `Microsoft.VisualStudio.Package.ProjectNode` usam os métodos de `Microsoft.Build.BuildEngine` (MSBuild) para obter e definir as propriedades de projeto e configuração do arquivo de projeto.  
  
  A classe derivada de `SettingsPage` deve implementar `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` e `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` para persistir as propriedades de projeto ou configuração do arquivo de projeto.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute e caminho do registro  
 Classes derivadas de `SettingsPage` são projetadas para serem compartilhadas entre VSPackages. Para possibilitar que um VSPackage crie uma classe derivada de `SettingsPage`, adicione um `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` a uma classe derivada de `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 O VSPackage ao qual o atributo está anexado não é importante. Quando um VSPackage é registrado com [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], a ID de classe (CLSID) de qualquer objeto que pode ser criado é registrada de forma que uma chamada para <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> possa criá-lo.  
  
 O caminho do registro de um objeto que pode ser criado é determinado pela combinação de <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, da palavra, do CLSID e do GUID do tipo de objeto. Se `MyProjectPropertyPage` classe tiver um GUID de {3c693da2-5bca-49B3-bd95-ffe0a39dd723} e UserRegistryRoot for HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp, o caminho do registro será HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49B3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Layout e atributos de propriedade de configuração e projeto  
 Os atributos <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>e <xref:System.ComponentModel.DescriptionAttribute> determinam o layout, a rotulação e a descrição do projeto e das propriedades de configuração em uma página de propriedades genérica. Esses atributos determinam a categoria, o nome de exibição e a descrição da opção, respectivamente.  
  
> [!NOTE]
> Atributos equivalentes, SRCategory, LocDisplayName e SRDescription, usam recursos de cadeia de caracteres para localização e são definidos em [MPF for projects-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Considere o fragmento de código a seguir:  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 A propriedade de configuração `MyConfigProp` aparece na página de propriedades de configuração como **minha propriedade** de configuração na categoria, **minha categoria**. Se a opção for selecionada, a descrição, **minha descrição**, aparecerá no painel Descrição.  
  
## <a name="see-also"></a>Consulte também  
 [Não está no Build: passo a passos: expondo o projetoC#e as propriedades de configuração ()](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Adicionando e removendo páginas de propriedades](../../extensibility/adding-and-removing-property-pages.md)   
   de [estado VSPackage](../../misc/vspackage-state.md)  
 [Projetos](../../extensibility/internals/projects.md)   
 [NIB: modelos do Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Arquivos de descrição do diretório do modelo (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
