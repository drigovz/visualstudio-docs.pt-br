---
title: Atualize modelos personalizados de projeto e itens para o Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698854"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Atualize modelos personalizados de projeto e itens para o Visual Studio 2017

A partir do Visual Studio 2017, o Visual Studio descobre modelos de projeto e itens que foram instalados por um .vsix ou um .msi de uma forma diferente das versões anteriores do Visual Studio. Se você possui extensões que usam modelos personalizados de projeto ou itens, você precisa atualizar suas extensões. Este artigo explica o que você deve fazer.

Essa mudança afeta apenas o Visual Studio 2017. Não afeta versões anteriores do Visual Studio.

Se você quiser criar um modelo de projeto ou item como parte de uma extensão VSIX, consulte [Criando modelos de projeto personalizado e de itens](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Varredura de modelos

Em versões anteriores do Visual Studio, **devenv /setup** ou **devenv /installvstemplates** digitalizaram o disco local para encontrar modelos de projeto e itens. A partir do Visual Studio 2017, a digitalização é realizada apenas para a localização do usuário. A localização padrão do nível do usuário é **%USERPROFILE%\Documentos\\<\>versão do Visual Studio \Templates\\**. Este local é usado para modelos gerados pelo comando **Project** > **Export Templates...** se a opção Importar automaticamente o modelo para o Visual **Studio** for selecionada no assistente.

Para outros locais (não usuários), você deve incluir um arquivo manifesto (.vstman) que especifica a localização e outras características do modelo. O arquivo .vstman é gerado juntamente com o arquivo .vstemplate usado para modelos. Se você instalar sua extensão usando um .vsix, você pode conseguir isso recompilando a extensão no Visual Studio 2017. Mas se você usar um .msi, você precisa fazer as mudanças manualmente. Para obter uma lista do que você precisa fazer para fazer essas alterações, consulte **Upgrades para extensões instaladas com um . MSI** mais tarde nesta página.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Como atualizar uma extensão VSIX com modelos de projeto ou itens

1. Abra a solução no Visual Studio 2017. Você será solicitado a atualizar o código. Clique em **OK**.

2. Depois que a atualização for concluída, talvez seja necessário alterar a versão do destino de instalação. No projeto VSIX, abra o arquivo source.extension.vsixmanifest e selecione a guia **'Instalar alvos'.** Se o campo **'Faixa de versão'** for **[14.0]** clique em **Editar** e alterá-lo para incluir o Visual Studio 2017. Por exemplo, você pode configurá-lo para **[14.0,15.0]** para instalar a extensão tanto no Visual Studio 2015 quanto no Visual Studio 2017, ou **em [15.0]** para instalá-lo apenas no Visual Studio 2017.

3. Recompile o código.

4. Feche o Visual Studio.

5. Instale o VSIX.

6. Você pode testar a atualização fazendo o seguinte:

    1. A alteração de digitalização de arquivos é ativada pela seguinte chave de registro:

         **reg adicionar hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DesativarTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Depois de adicionar a chave, execute **os modelos devenv /installvs .**

    3. Reabra o Visual Studio. Você deve encontrar seu modelo no local esperado.

    > [!NOTE]
    > Os modelos de projeto visual studio extensibility não estão disponíveis quando a chave de registro está presente. Você deve excluir a chave de registro (e reexecutar **devenv /installvstemplates)** para usá-las.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Outras recomendações para implantação de modelos de projeto e itens

- Evite usar arquivos de modelo com zíper. Os arquivos de modelo com zíper precisam ser descompactados para recuperar recursos e conteúdo, para que sejam mais caros de usar. Em vez disso, você deve implantar modelos de projeto e itens como arquivos individuais sob seu próprio diretório para acelerar a inicialização do modelo. Para extensões VSIX, as tarefas de compilação do SDK descompactarão automaticamente qualquer modelo com zíper enquanto cria o arquivo VSIX.

- Evite usar entradas de iD de pacote/recurso para o nome do modelo, descrição, ícone ou visualização para evitar cargas desnecessárias de montagem de recursos durante a detecção do modelo. Em vez disso, você pode usar manifestos localizados para criar uma entrada de modelo para cada local, que usa nomes ou propriedades localizadas.

- Se você estiver incluindo modelos como itens de arquivo, a geração manifesto pode não lhe dar os resultados esperados. Nesse caso, você terá que adicionar um manifesto gerado manualmente ao projeto VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Alterações de arquivo em modelos de projeto e itens
Mostramos os pontos de diferença entre as versões visual studio 2015 e visual studio 2017 dos arquivos de modelo, para que você possa criar os novos arquivos corretamente.

 Aqui está o arquivo padrão do projeto .vstemplate criado pelo Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 Aqui está o arquivo .vstman (você pode encontrá-lo no diretório manifesto do projeto VSIX) que resultou da reconstrução do projeto VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 As informações fornecidas pelo elemento [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) permanecem as mesmas. O ** \<elemento VSTemplateContainer>** aponta para o arquivo .vstemplate para o modelo associado.

 Aqui está o arquivo padrão do item .vstemplate criado pelo Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 Aqui está o arquivo .vstman (você pode encontrá-lo no diretório manifesto do projeto VSIX) que resultou da reconstrução do projeto VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 As informações fornecidas ** \<** pelo elemento TemplateData>permanecem as mesmas. O ** \<elemento VSTemplateContainer>** aponta para o arquivo .vstemplate para o modelo associado

 Para obter mais informações sobre os diferentes elementos do arquivo .vstman, consulte [Visual Studio Template Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Upgrades para extensões instalados com um . Msi

Algumas extensões baseadas em MSI implantam modelos em locais de modelo comuns, como os seguintes diretórios:

- **\<Diretório de instalação do Visual Studio\\>\Common7\IDE<ProjectTemplates/ItemTemplates\>**

- **\<Diretório de instalação do Visual Studio>\Common7\IDE\Extensões<ExtensãoNome\\ \> \\<Projetos/Modelos\>**

Se a extensão realizar uma implantação baseada em MSI, você precisa gerar o manifesto do modelo manualmente e garantir que ele esteja incluído na configuração de extensão. Compare os exemplos .vstman listados acima e o [Visual Studio Template Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

Crie manifestos separados para modelos de projeto e itens, e eles devem apontar para o diretório de modeloraiz, conforme especificado acima. Crie um manifesto por extensão e local.

## <a name="see-also"></a>Confira também

- [Descoberta de modelo de solução de problemas](troubleshooting-template-discovery.md)
- [Criando modelos personalizados de projetos e itens](creating-custom-project-and-item-templates.md)
