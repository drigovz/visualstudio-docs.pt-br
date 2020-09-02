---
title: Elemento RequiredPlatformVersion (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e5ba8cfef6674b5603cf03c73619f686338af3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159281"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (Modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica a versão mínima do sistema operacional que o modelo de projeto requer para funcionar corretamente. Esse elemento é usado para modelos de projeto que criam [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplicativos.  
  
 O `RequiredPlatformVersion` valor é comparado diretamente com a versão do sistema operacional. Se o `RequiredPlatformVersion` for maior que a versão do sistema operacional, o modelo não aparecerá na caixa de diálogo **novo projeto** . Para especificar um modelo para o [!INCLUDE[win8](../includes/win8-md.md)] ou superior, defina `RequiredPlatformVersion` como 6.2.0. Para especificar um modelo para [!INCLUDE[win81](../includes/win81-md.md)] ou superior, defina RequiredPlatformVersion como 6.3.0.  
  
 Modelos que especificam `RequiredPlatformVersion` = 8 são compatíveis com modelos de cliente anteriores [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 Nenhum.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica a plataforma de destino do modelo de projeto.|  
  
## <a name="text-value"></a>Valor de texto  
 Um valor de texto é obrigatório.  
  
## <a name="remarks"></a>Comentários  
 Esse texto especifica a versão mínima do sistema operacional exigida pelo modelo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo especifica que o modelo de projeto tem como destino [!INCLUDE[win8](../includes/win8-md.md)] ou posterior.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Elemento TargetPlatformName (modelos do Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Criando modelos de projeto e item](../ide/creating-project-and-item-templates.md)   
 [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
