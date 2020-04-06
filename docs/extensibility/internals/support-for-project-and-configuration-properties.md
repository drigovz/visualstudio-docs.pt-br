---
title: Suporte para propriedades de projeto e configuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704897"
---
# <a name="support-for-project-and-configuration-properties"></a>Suporte para propriedades do projeto e de configuração
A **Properties** janela Propriedades [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no ambiente de desenvolvimento integrado (IDE) pode exibir propriedades de projeto e configuração. Você pode fornecer uma página de propriedade para o seu próprio tipo de projeto para que o usuário possa definir propriedades para o seu aplicativo.

 Selecionando um nó de projeto no **Solution Explorer** e, em seguida, clicando em **Propriedades** no menu **Projeto,** você pode abrir uma caixa de diálogo que inclui propriedades de projeto e configuração. Dentro [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]e , e tipos de projeto derivados desses idiomas, esta caixa de diálogo aparece como uma página com guias na [Caixa de Diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md). Para obter mais informações, consulte [Não em Construção: Passo a passo: Expondo propriedades de projeto e configuração (C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 O MpfProj (Managed Package Framework for Projects) oferece aulas de ajuda para a criação e gerenciamento de novos sistemas de projetos. Você pode encontrar o código fonte e instruções de compilação no [MPF para Projetos - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Persistência das propriedades de projeto e configuração
 As propriedades de projeto e configuração são persistidas em um arquivo de projeto que tenha qualquer extensão de nome de arquivo associada ao tipo de projeto, por exemplo, .csproj, .vbproj e .myproj. Os projetos de idioma normalmente usam um arquivo de modelo para gerar o arquivo do projeto. No entanto, existem várias maneiras de associar tipos de projetos e modelos. Para obter mais informações, consulte [Template Directory Description (. Vsdir) Arquivos](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 As propriedades de projeto e configuração são criadas adicionando itens ao arquivo de modelo. Essas propriedades estão então disponíveis para qualquer projeto criado usando o tipo de projeto que usa esse modelo. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]projetos e o MPFProj usam o esquema [Não em Construção: MSBuild Visão geral](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) para arquivos de modelo. Esses arquivos têm uma seção PropertyGroup para cada configuração. As propriedades dos projetos são normalmente persistidas na primeira seção PropertyGroup, que tem um argumento de configuração definido como uma seqüência de string nula.

 O código a seguir mostra o início de um arquivo básico do projeto MSBuild.

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

 Neste arquivo de `<Name>` `<SchemaVersion>` projeto, e `<Optimize>` são propriedades do projeto, e é uma propriedade de configuração.

 É responsabilidade do projeto persistir as propriedades de projeto e configuração do arquivo do projeto.

> [!NOTE]
> Um projeto pode otimizar a persistência apenas de valores de propriedade que diferem de seus valores padrão.

## <a name="support-for-project-and-configuration-properties"></a>Suporte para propriedades do projeto e de configuração
 A `Microsoft.VisualStudio.Package.SettingsPage` classe implementa páginas de propriedade de projeto e configuração. A implementação `SettingsPage` padrão de oferece propriedades públicas a um usuário em uma grade de propriedade genérica. O `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` método seleciona classes `SettingsPage` derivadas para grades de propriedade de projetos. O `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` método seleciona classes `SettingsPage` derivadas para grades de propriedade de configuração. Seu tipo de projeto deve substituir esses métodos para selecionar as páginas de propriedade apropriadas.

 A `SettingsPage` classe `Microsoft.VisualStudio.Package.ProjectNode` e a classe oferecem esses métodos para persistir as propriedades de projeto e configuração:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` persistir propriedades do projeto.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` persistir propriedades de configuração.

  > [!NOTE]
  > As implementações `Microsoft.VisualStudio.Package.SettingsPage` das `Microsoft.VisualStudio.Package.ProjectNode` classes `Microsoft.Build.BuildEngine` e das classes usam os métodos (MSBuild) para obter e definir propriedades de projeto e configuração a partir do arquivo do projeto.

  A classe da `SettingsPage` sua `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` origem deve implementar e persistir as propriedades de projeto ou configuração do arquivo do projeto.

## <a name="provideobjectattribute-and-registry-path"></a>Fornecercaminho de atributo e registro de objetode objeto
 As classes `SettingsPage` derivadas são projetadas para serem compartilhadas entre VSPackages. Para tornar possível que um VSPackage crie `SettingsPage`uma classe `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` derivada, adicione `Microsoft.VisualStudio.Shell.Package`a a uma classe derivada de .

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 O VSPackage ao qual o atributo é anexado não é importante. Quando um VSPackage é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]registrado com , o id de classe (CLSID) de qualquer objeto <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> que possa ser criado é registrado para que uma chamada possa criá-lo.

 O caminho de registro de um objeto que <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>pode ser criado é determinado pela combinação , a palavra, CLSID e o guia do tipo de objeto. Se `MyProjectPropertyPage` a classe tiver uma orientação de {3c693da2-5bca-49b3-bd95-ffe0a39dd72} e o UserRegistryRoot é HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, em seguida, o caminho\\do registro seria HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID {3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Atributos e layout de propriedades de projeto e configuração
 Os <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute>, <xref:System.ComponentModel.DescriptionAttribute> e atributos determinam o layout, rotulagem e descrição das propriedades de projeto e configuração em uma página de propriedade genérica. Esses atributos determinam a categoria, o nome de exibição e a descrição da opção, respectivamente.

> [!NOTE]
> Atributos equivalentes, SRCategory, LocDisplayName e SRDescription, usam recursos de string para localização e são definidos no [MPF para Projetos - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Considere o fragmento de código a seguir:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 A `MyConfigProp` propriedade configuração aparece na página de configuração como **My Config Property** na **categoria, Minha categoria**. Se a opção for selecionada, a descrição, **Minha Descrição,** aparecerá no painel de descrição.

## <a name="see-also"></a>Confira também
- [Adicionar e remover páginas de propriedade](../../extensibility/adding-and-removing-property-pages.md)
- [Projetos](../../extensibility/internals/projects.md)
- [Arquivos de descrição do diretório de modelo (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
