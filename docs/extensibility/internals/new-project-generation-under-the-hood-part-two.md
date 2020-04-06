---
title: 'Nova geração de projetos: Sob o Capô, Parte Dois | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707017"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Geração de novo projeto: nos bastidores, Parte dois

Em [New Project Generation: Under the Hood, Part One vimos](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) como a caixa de diálogo do Novo **Projeto** é preenchida. Vamos supor que você selecionou um **aplicativo visual C# Windows,** preencheu as caixas de texto **nome** e **localização** e clicou EM OK.

## <a name="generating-the-solution-files"></a>Gerando os arquivos de solução
 A escolha de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um modelo de aplicativo direciona para descompactar e abrir o arquivo .vstemplate correspondente e para lançar um modelo para interpretar os comandos XML neste arquivo. Esses comandos criam projetos e itens de projeto na solução nova ou existente.

 O modelo descompacta arquivos de origem, chamados modelos de item, da mesma pasta .zip que contém o arquivo .vstemplate. O modelo copia esses arquivos para o novo projeto, personalizando-os de acordo.

### <a name="template-parameter-replacement"></a>Substituição do parâmetro do modelo
 Quando o modelo copia um modelo de item para um novo projeto, ele substitui quaisquer parâmetros de modelo por strings para personalizar o arquivo. Um parâmetro de modelo é um token especial que é precedido e seguido por um sinal de dólar, por exemplo, $date$.

 Vamos olhar para um modelo típico de item do projeto. Extrair e examinar Program.cs na pasta Arquivos do Programa\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip folder.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

Se você criar um novo projeto de aplicativo `$safeprojectname$` do Windows chamado Simple, o modelo substituirá o parâmetro pelo nome do projeto.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 Para obter uma lista completa de parâmetros do modelo, consulte [Parâmetros de modelo](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Um olhar dentro de um . Arquivo VSTemplate
 Um arquivo básico .vstemplate tem esse formato

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Analisamos a \<seção TemplateData> na [Nova Geração de Projetos: Sob o Capô, Parte Um](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). As tags nesta seção são usadas para controlar a aparência da caixa de diálogo **Novo Projeto.**

 As tags \<na seção TemplateContent> controlam a geração de novos projetos e itens do projeto. Aqui está \<a seção TemplateContent> do arquivo cswindowsapplication.vstemplate no \Program Files\Microsoft Visual Studio 8\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip folder.

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 O \<Projeto> tag controla a geração \<de um projeto, e o ProjectItem> tag controla a geração de um item do projeto. Se o parâmetro ReplaceParameters for verdadeiro, o modelo personalizará todos os parâmetros do modelo no arquivo ou item do projeto. Neste caso, todos os itens do projeto são personalizados, exceto configurações.configurações.

 O parâmetro TargetFileName especifica o nome e o caminho relativo do arquivo ou item do projeto resultante. Isso permite que você crie uma estrutura de pasta para o seu projeto. Se você não especificar esse argumento, o item do projeto terá o mesmo nome do modelo de item do projeto.

 A estrutura de pasta de aplicativos do Windows resultante é assim:

 ![Solução simples](../../extensibility/internals/media/simplesolution.png "Solução simples")

 A primeira \<e única tag project> no modelo diz:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Isso instrui o modelo Do Novo Projeto a criar o arquivo de projeto Simple.csproj copiando e personalizando o item de modelo windowsapplication.csproj.

### <a name="designers-and-references"></a>Designers e Referências
 Você pode ver no Solution Explorer que a pasta Propriedades está presente e contém os arquivos esperados. Mas e as referências de projetos e dependências de arquivos de designer, como Resources.Designer.cs ao Resources.resx, e Form1.Designer.cs a Form1.cs?  Estes são configurados no arquivo Simple.csproj quando ele é gerado.

 Aqui está \<o itemGroup> do Simple.csproj que cria as referências do projeto:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Você pode ver que essas são as seis referências de projeto que aparecem no Solution Explorer. Aqui está uma seção de outro \<ItemGroup>. Muitas linhas de código foram excluídas para clareza. Esta seção torna Settings.Designer.cs dependente de Configurações.configurações:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Confira também

- [Geração de novo projeto: nos bastidores, Parte um](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
