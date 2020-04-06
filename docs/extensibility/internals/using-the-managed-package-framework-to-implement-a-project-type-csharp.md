---
title: Usando o Managed Package Framework for a Project Type (C#) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704116"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Usando a estrutura de pacote gerenciado para implementar um tipo de projeto (C#)
O MPF (Managed Package Framework, quadro de pacotes gerenciados) fornece classes C# que você pode usar ou herdar para implementar seus próprios tipos de projeto. O MPF implementa muitas das interfaces que o Visual Studio espera que um tipo de projeto forneça, deixando você livre para se concentrar na implementação das particularidades do seu tipo de projeto.

## <a name="using-the-mpf-project-source-code"></a>Usando o Código Fonte do Projeto MPF
 O MpfProj (Managed Package Framework for Projects) oferece aulas de ajuda para a criação e gerenciamento de novos sistemas de projetos. Ao contrário de outras turmas do MPF, as aulas do projeto não estão incluídas nas montagens enviadas com o Visual Studio. Em vez disso, as aulas do projeto são fornecidas como código fonte no [MPF para projetos 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Para adicionar este projeto à sua solução VSPackage, faça o seguinte:

1. Baixe os arquivos MPFProj para *MPFProjectDir*.

2. No *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, altere o seguinte bloco:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Crie um projeto VSPackage.

2. Descarregue o projeto VSPackage.

3. Edite o arquivo VSPackage .csproj adicionando `<Import>` o seguinte bloco antes dos outros blocos:

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1. Salve o projeto.

2. Feche e reabra a solução VSPackage.

3. Reabra o projeto VSPackage. Você deve ver um novo diretório chamado ProjectBase.

4. Adicione a seguinte referência ao projeto VSPackage:

     Microsoft.Build.Tasks.4.0

5. Compile o projeto.

## <a name="hierarchy-classes"></a>Classes de Hierarquia
 A tabela a seguir resume as classes no MPFProj que suportam hierarquias de projetos. Para obter mais informações, consulte [Hierarquias e Seleção](../../extensibility/internals/hierarchies-and-selection.md).

|Nome da classe|
|----------------|
|`Microsoft.VisualStudio.Package.HierarchyNode`|
|`Microsoft.VisualStudio.Package.ProjectNode`|
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|
|`Microsoft.VisualStudio.Package.FileNode`|
|`Microsoft.VisualStudio.Package.FolderNode`|
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|
|`Microsoft.VisualStudio.Package.ReferenceNode`|
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|
|`Microsoft.VisualStudio.Package.ComReferenceNode`|
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|
|`Microsoft.VisualStudio.Package.BuildDependency`|

## <a name="document-handling-classes"></a>Aulas de manipulação de documentos
 A tabela a seguir lista as classes do MPF que apoiam o manuseio de documentos. Para obter mais informações, consulte [Itens do projeto de abertura e salvamento](../../extensibility/internals/opening-and-saving-project-items.md).

|Nome da classe|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Classes de configuração e saída
 A tabela a seguir lista as classes do MPF que permitem que os tipos de projeto suportem várias configurações, como depuração e liberação, e coleções de saída de projeto. Para obter mais informações, consulte [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md).

|Nome da classe|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Aulas de suporte à automação
 A tabela a seguir lista as classes do MPF que suportam automação para que os usuários do seu tipo de projeto possam escrever complementos.

|Nome da classe|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Classes de propriedades
 A tabela a seguir lista as classes no MPF que permitem que os tipos de projeto adicionem propriedades que os usuários podem navegar e modificar em um navegador de propriedade.

|Nome da classe|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
