---
title: Elemento CustomParameter (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59bfec972750a4f893d1cb8b7cf08710bcca761a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555954"
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento CustomParameter (modelos do Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contém um nome de parâmetro personalizado e um valor a ser usado quando um projeto ou item é criado a partir do modelo.  
  
## <a name="syntax"></a>Syntax  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Obrigatórios. O nome do parâmetro. O formato dos parâmetros é $*Name*$.|  
|`Value`|Obrigatórios. O valor de substituição para o parâmetro.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Agrupa os parâmetros personalizados que devem ser passados para o assistente de modelo quando o assistente faz substituições de parâmetro.|  
  
## <a name="remarks"></a>Comentários  
 Quando um modelo contém `CustomParameter` elementos, cada instância do `Name` atributo é substituída pelo `Value` atributo no projeto ou nos arquivos de item criados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar vários parâmetros personalizados em um modelo. Quando um projeto ou item é criado a partir de um modelo com os seguintes parâmetros personalizados, todas as instâncias de `$color1$` e `$color2$` nos arquivos de modelo serão substituídas por `Red` e `Blue` , respectivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Elemento CustomParameters (modelos do Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parâmetros de modelo](../ide/template-parameters.md)   
 [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
