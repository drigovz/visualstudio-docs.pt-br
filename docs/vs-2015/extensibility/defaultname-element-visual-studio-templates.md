---
title: Elemento DefaultName (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bc3a18c47b78a312f3bca3762cc4ff3d658a70e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185296"
---
# <a name="defaultname-element-visual-studio-templates"></a>Elemento DefaultName (modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica o nome que o sistema de projeto do Visual Studio gerará para o projeto ou item quando ele for criado.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<DefaultName>  
  
## <a name="syntax"></a>Syntax  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necessário.<br /><br /> Categoriza o modelo e define como ele é exibido no **novo projeto** ou na caixa de diálogo **Adicionar novo item** .|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
 Esse texto especifica o nome padrão do projeto ou do item.  
  
## <a name="remarks"></a>Comentários  
 `DefaultName` é um elemento opcional.  
  
 Para projetos, esse elemento Especifica o nome do diretório que armazena o projeto em disco. Para itens, ele especifica o nome do arquivo de origem.  
  
 Ao criar um projeto ou item, você pode modificar o nome padrão usando a opção **nome** , que está disponível na caixa de diálogo **novo projeto** ou **Adicionar novo item** .  
  
 Se você não quiser que o sistema de projeto gere o nome padrão para o projeto ou item, defina o elemento [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) como `False` .  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra os metadados para o modelo de item padrão para uma [!INCLUDE[csprcs](../includes/csprcs-md.md)] classe.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
