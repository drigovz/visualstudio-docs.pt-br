---
title: Elemento LocalizedName (esquema de pacote de idiomas do VSIX) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d17ce9db334d3b2cc8b6c892784b10d42eba07ad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832414"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Elemento LocalizedName (esquema de pacote de idiomas do VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Necessário. O nome localizado da extensão a ser instalado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Nenhum||  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento LanguagePack do VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Necessário. Fornece o elemento raiz para um pacote de idiomas do VSIX.|  
  
## <a name="text-value"></a>Valor de texto  
 Necessário. O nome do pacote de idiomas no idioma de destino.  
  
## <a name="element-information"></a>Informações do elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Namespace    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Nome do esquema   |                 Esquema de pacote de idiomas do VSIX                 |
| Arquivo de validação |                VSIXLanguagePackSchema.xsd                 |
|  Pode ser vazio   |                      Não aplicável                       |
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema do pacote de idioma VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizar pacotes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referência de esquema 1.0 de extensão do VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

