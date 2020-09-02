---
title: CreateInPlace (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d722aebef0cbcf589185c36cb481a676280d59ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184243"
---
# <a name="createinplace-visual-studio-templates"></a>CreateInPlace (modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica se deseja criar o projeto e executar a substituição de parâmetro no local especificado, ou executar a substituição de parâmetro em um local temporário e, em seguida, salvar o projeto no local especificado.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<CreateInPlace>  
  
## <a name="syntax"></a>Syntax  
  
```  
<CreateInPlace> true/false </CreateInPlace>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido no **novo projeto** ou na caixa de diálogo **Adicionar novo item** .|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 O texto deve ser `true` ou `false` . Se `true` , o projeto é criado e a substituição de parâmetro é executada no local especificado na caixa de diálogo **novo projeto** . Se `false` , a substituição de parâmetro será executada em um local temporário e o projeto será copiado para o local especificado.  
  
## <a name="remarks"></a>Comentários  
 `CreateInPlace` é um elemento opcional. O valor padrão é `true`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra os metadados de um [!INCLUDE[csprcs](../includes/csprcs-md.md)] modelo.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <CreateInPlace>false</CreateInPlace>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Criando modelos de projeto e item](../ide/creating-project-and-item-templates.md)   
 [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
