---
title: Atualizando projeto personalizados e modelos de Item para Visual Studio 2017 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: cb4defa206d176e57804e6d2473262568cd5edbf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434209"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Atualizar modelos de Item para Visual Studio 2017 e projeto personalizados

A partir do Visual Studio 2017, Visual Studio detecta os modelos de projeto e item que foram instalados por um VSIX ou um. msi de uma maneira diferente para versões anteriores do Visual Studio. Se você possui as extensões que usam modelos de item ou de projeto personalizado, você precisará atualizar suas extensões. Este artigo explica o que você deve fazer.

Essa alteração afeta apenas o Visual Studio 2017. Ele não afeta as versões anteriores do Visual Studio.

Se você quiser criar um modelo de projeto ou item como parte de uma extensão do VSIX, consulte [personalizados de criação de projeto e modelos de Item](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Verificação de modelo

Nas versões anteriores do Visual Studio, **devenv /setup** ou **devenv /installvstemplates** verificados no disco local para localizar modelos de projeto e item. A partir do Visual Studio 2017, a verificação é executada somente para o local de nível de usuário. O local de nível de usuário padrão é **%USERPROFILE%\Documents\\< versão do Visual Studio\>\Templates\\**. Esse local é usado para modelos gerados pelo **Project** > **exportar modelos...**  comando, se o **importar automaticamente o modelo no Visual Studio** opção for selecionada no assistente.

Para outros locais (não-usuário), você deve incluir um arquivo de manifest(.vstman) que especifica o local e outras características do modelo. O arquivo vstman é gerado, juntamente com o arquivo. vstemplate usado para modelos. Se você instalar a extensão usando um. VSIX, você pode fazer isso por meio da recompilação a extensão no Visual Studio 2017. Mas se você usar um. msi, você precisa fazer as alterações manualmente. Para obter uma lista do que você precisa fazer para que essas alterações, consulte **atualizações para extensões instaladas com um. MSI** posteriormente nesta página.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Como atualizar uma extensão do VSIX com modelos de Item ou projeto

1. Abra a solução no Visual Studio 2017. Você será solicitado a atualizar o código. Clique em **OK**.

2. Após a conclusão da atualização, você precisa alterar a versão de destino de instalação. No projeto VSIX, abra o arquivo vsixmanifest e selecione o **instalar destinos** guia. Se o **intervalo de versão** campo é **[14.0]**, clique em **editar** e alterá-lo para incluir o Visual Studio 2017. Por exemplo, ele pode ser definido como **[14.0,15.0]** para instalar a extensão do Visual Studio 2015 ou Visual Studio 2017, ou em **[15.0]** para instalá-lo para apenas o Visual Studio 2017.

3. Recompile o código.

4. Feche o Visual Studio.

5. Instale o VSIX.

6. Você pode testar a atualização, fazendo o seguinte:

    1. Verificação de alteração de arquivo é ativado pela seguinte chave do registro:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Depois de adicionar a chave, execute **devenv /installvstemplates**.

    3. Reabra o Visual Studio. Você deve encontrar o modelo no local esperado.

    > [!NOTE]
    > Os modelos de projeto de extensibilidade do Visual Studio não estão disponíveis quando a chave do registro está presente. Você deve excluir a chave do registro (e executar novamente **devenv /installvstemplates**) para usá-los.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Outras recomendações para a implantação de modelos de projeto e Item

- Evite usar arquivos de modelo compactado. Compactado arquivos precisam ser descompactado para recuperar os recursos e o conteúdo do modelo, portanto, eles serão mais caras usar. Em vez disso, você deve implantar os modelos de projeto e item como arquivos individuais em seu próprio diretório para acelerar a inicialização de modelo. Extensões de VSIX, tarefas de build do SDK descompactará automaticamente qualquer modelo compactado ao criar o arquivo VSIX.

- Evite usar entradas de ID de recurso do pacote para o nome do modelo, a descrição, o ícone ou visualizar a fim de evitar carregamentos de assembly de recurso desnecessárias durante a descoberta de modelo. Em vez disso, você pode usar manifestos localizados para criar uma entrada de modelo para cada localidade, que usa nomes localizados ou propriedades.

- Se você estiver incluindo modelos como itens de arquivo, geração de manifesto não pode fornecer os resultados esperados. Nesse caso, você terá que adicionar um manifesto gerado manualmente para o projeto VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Alterações de arquivo no projeto e modelos de Item
Mostramos os pontos da diferença entre o Visual Studio 2015 e Visual Studio 2017 versões dos arquivos de modelo, para que você possa criar novos arquivos corretamente.

 Aqui está o arquivo. vstemplate de projeto padrão criado pelo Visual Studio 2015:

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

 Aqui está o arquivo de vstman (você pode encontrá-lo no diretório de manifesto do projeto VSIX) que resultaram da recriação do projeto VSIX:

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

 As informações fornecidas pelo [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elemento permanece o mesmo. O  **\<VSTemplateContainer >** elemento aponta para o arquivo. vstemplate para o modelo associado.

 Aqui está o arquivo. vstemplate de item de padrão criado pelo Visual Studio 2015:

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

 Aqui está o arquivo de vstman (você pode encontrá-lo no diretório de manifesto do projeto VSIX) que resultaram da recriação do projeto VSIX:

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

 As informações fornecidas pelo  **\<TemplateData >** elemento permanece o mesmo. O  **\<VSTemplateContainer >** elemento aponta para o arquivo. vstemplate para o modelo associado

 Para obter mais informações sobre os diferentes elementos do arquivo vstman, consulte [modelo de manifesto do esquema de referência do Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Atualizações para as extensões instaladas com um. MSI

Algumas extensões baseadas em MSI implantar modelos em locais de modelo comuns, como os diretórios a seguir:

- **\<Diretório de instalação do Visual Studio > \Common7\IDE\\< ProjectTemplates/ItemTemplates >**

- **\<Diretório de instalação do Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< Project/ItemTemplates >**

Se sua extensão executa uma implantação baseada em MSI, você precisa gerar o manifesto do modelo manualmente e certifique-se de que ele seja incluído na configuração da extensão. Compare os exemplos de vstman listados acima e o [modelo de manifesto do esquema de referência do Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Criar manifestos separados para modelos de projeto e item, e eles devem apontar para o modelo diretório raiz conforme especificado acima. Crie um manifesto por extensão e a localidade.

## <a name="see-also"></a>Consulte também

- [Descoberta do modelo de solução de problemas](troubleshooting-template-discovery.md)
- [Criando modelos personalizados de projeto e de item](creating-custom-project-and-item-templates.md)