---
title: Elemento VSIXLanguagePack (esquema de pacote de idiomas do VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b4ba4e98b8b2d42485a7594d5bab658e1bd6ccb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422481"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Elemento VSIXLanguagePack (esquema de pacote de idiomas do VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Necessário. Fornece o elemento raiz para um pacote de idiomas do VSIX. O pacote de idiomas do VSIX fornece informações de instalação localizada para um pacote VSIX.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`xmlns`|O namespace XML no qual o esquema do pacote de idiomas do VSIX está definido.|  
  
## <a name="xmlns-attribute"></a>Atributo xmlns  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Necessário. O local do arquivo que define o esquema para pacotes de idiomas.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Necessário. O nome localizado da extensão a ser instalado.|  
|[Elemento LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Necessário. A descrição localizada da extensão a ser instalado.|  
|[Elemento MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Opcional. Um link para informações localizadas sobre a extensão.|  
|[Elemento License](../extensibility/license-element-vsix-language-pack-schema.md)|Opcional. O caminho de uma versão localizada do arquivo de licença para a extensão.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum||  
  
## <a name="element-information"></a>Informações do elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Namespace    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Nome do esquema   |                 Esquema de pacote de idiomas do VSIX                 |
| Arquivo de validação |                VSIXLanguagePackSchema.xsd                 |
|  Pode ser vazio   |                            Não                             |
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema do pacote de idioma VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizar pacotes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referência de esquema 1.0 de extensão do VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
