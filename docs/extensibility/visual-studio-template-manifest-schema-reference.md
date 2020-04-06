---
title: Visual Studio Template Manifest Schema Reference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697980"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Modelo visual Studio manifesta referência de esquema
Este esquema descreve o formato do manifesto de modelo do Visual Studio *(.vstman)* arquivos gerados para modelos de projeto ou itens do Visual Studio. O esquema também descreve a localização e outras informações relevantes sobre o modelo.

 : Como existem diretórios separados de itens e modelos de projeto, um manifesto nunca deve ter uma mistura de itens e modelos de projeto.

> [!IMPORTANT]
> Este manifesto está disponível a partir do Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Elemento VSTemplateManifest
 O elemento raiz do manifesto.

### <a name="attributes"></a>Atributos

- **Versão**: Uma seqüência representando a versão do manifesto do modelo. Obrigatórios.

- **Locale**: Uma seqüência representando a localidade ou as localidades do manifesto do modelo. O valor da localização se aplica a todos os modelos. Você deve usar um manifesto separado para cada localidade. Opcional.

### <a name="child-elements"></a>Elementos filho

- **VSTemplateContainer** Opcional.

- **VSTemplateDir** Opcional.

### <a name="parent-element"></a>Elemento pai
 Nenhum.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 O recipiente do modelo manifesta elementos. Um manifesto tem um recipiente de modelo para cada modelo que define.

### <a name="attributes"></a>Atributos
 **VSTemplateType**: Um valor de string que`"Project"`especifica `"Item"`o `"ProjectGroup"`tipo do modelo (, ou ). Obrigatório

### <a name="child-elements"></a>Elementos filho

- **RelativePathOnDisk**: O caminho relativo do arquivo de modelo em disco. Este local também define a colocação do modelo na árvore de modelo mostrada na caixa de diálogo **Novo Projeto** ou **Novo Item.** Para modelos implantados como um diretório e arquivos individuais, este caminho refere-se ao diretório que contém os arquivos de modelo. Para modelos implantados como um arquivo *.zip,* este caminho deve ser o caminho para o arquivo *.zip.*

- **VSTemplateHeader: um elemento [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) que descreve o cabeçalho.

### <a name="parent-element"></a>Elemento pai
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Descreve o diretório onde o modelo está localizado. Um manifesto pode conter várias entradas **VSTemplateDir** para fornecer nome localizado e ordenar a ordem para que os diretórios controlem sua aparência na árvore de categoria de modelo.

 Devido ao seu design, as entradas **VSTemplateDir** devem aparecer apenas em manifestos não localizados especificados.

### <a name="attributes"></a>Atributos
 Nenhum.

### <a name="child-elements"></a>Elementos filho

- **RelativePath**: O caminho do modelo. Só pode haver uma entrada por caminho, então a primeira ganhará para todos os manifestos.

- **Nome localizado:** um elemento **NameDescriptionIcon** que especifica o nome localizado. Opcional.

- **SortOrder**: Uma seqüência que especifica a ordem de classificação. Opcional.

- **ParentFolderOverrideName**: O nome substituído da pasta-mãe. Opcional. Este elemento tem um atributo **Nome,** que é um valor de string que especifica o nome.

### <a name="parent-element"></a>Elemento pai
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>Ícone de nome
 Especifica o nome e a descrição, possivelmente para modelos localizados. Consulte **LocalizedName** acima.

### <a name="attributes"></a>Atributos

- **Pacote**: Um valor de corda que especifica o pacote. Opcional.

- **ID**: Um valor de string que especifica o ID. Opcional.

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-element"></a>Elemento pai
 **Localizedname**

## <a name="examples"></a>Exemplos
 O código a seguir é um exemplo de um arquivo de modelo de projeto *.vstman.*

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 O código a seguir é um exemplo de um modelo de item *.vstman* file.

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
