---
title: Elemento MaxFrameworkVersion (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194325"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica a versão máxima do .NET Framework exigido pelo modelo. Ele determina se o modelo é exibido na seção **modelos** da caixa de diálogo **Adicionar novo projeto** , com base no valor selecionado na caixa **versão da estrutura de destino** da caixa de diálogo **Adicionar novo projeto** .  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
## <a name="syntax"></a>Syntax  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
  
 O texto deve ser o número de versão mais alto do .NET Framework permitido pelo modelo.  
  
## <a name="remarks"></a>Comentários  
 `MaxFrameworkVersion` é um elemento opcional. O elemento na `TemplateData` seção do arquivo. vstemplate atua como um filtro para a seção **modelos** da caixa de diálogo **Adicionar novo projeto** . Somente modelos cujos requisitos de .NET Framework são menores que `MaxFrameworkVersion` valores de elemento serão exibidos, com base no valor selecionado na caixa **versão da estrutura de destino** da caixa de diálogo **Adicionar novo projeto** . O `MaxFrameworkVersion` elemento deve ser omitido, a menos que seja necessário, de modo que não fazer com que modelos sejam exibidos inadvertidamente quando eles são usados com versões mais recentes do .NET Framework.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra os metadados para um [!INCLUDE[csprcs](../includes/csprcs-md.md)] modelo de classe padrão.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Neste exemplo, a versão máxima do .NET Framework exigido pelo modelo, representada por `MaxFrameworkVersion` , é 3,5. O modelo acima será exibido somente quando você selecionar 3,0 ou 3,5 na caixa versão da **estrutura de destino** na caixa de diálogo **Adicionar novo projeto** .  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
