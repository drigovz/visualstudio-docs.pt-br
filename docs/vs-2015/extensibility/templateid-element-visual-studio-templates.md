---
title: Elemento TemplateID (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a52b360994c53eef69ceafa45828ec1020be16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186419"
---
# <a name="templateid-element-visual-studio-templates"></a>Elemento TemplateID (modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica um identificador para um modelo de item que é categorizado em um grupo de modelos de item pelo elemento [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateID>  
  
## <a name="syntax"></a>Syntax  
  
```  
<TemplateID> ... </TemplateID>  
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
 Um `string` que representa um identificador para um modelo de item que é categorizado em um grupo de modelos de item pelo `TemplateGroupID` elemento.  
  
## <a name="remarks"></a>Comentários  
 `TemplateID` é um elemento opcional.  
  
 Se um arquivo. vstemplate omitir o `TemplateID` elemento, o elemento [Name](../extensibility/name-element-visual-studio-templates.md) será usado como o identificador para o modelo.  
  
 O valor do `TemplateID` elemento é usado junto com o registro do sistema de projeto (HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\11.0\Projects \\ ) para filtrar os modelos que aparecem na caixa de diálogo **Adicionar novo item** .  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
