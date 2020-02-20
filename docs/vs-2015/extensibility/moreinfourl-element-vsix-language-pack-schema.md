---
title: Elemento MoreInfoURL (esquema do pacote de idiomas do VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 3f07b67b-95c5-4ae8-8b7e-d643cbbb0348
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c583d67e1920080f11158a4001e191e93e234006
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476837"
---
# <a name="moreinfourl-element-vsix-language-pack-schema"></a>Elemento MoreInfoURL (esquema do pacote de idiomas do VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcional. Um link para informações localizadas sobre a extensão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<MoreInfoURL>URL</MoreInfoURL>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|DESCRIÇÃO|  
|---------------|-----------------|  
|Nenhum||  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|DESCRIÇÃO|  
|-------------|-----------------|  
|Nenhum||  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|Elemento|DESCRIÇÃO|  
|-------------|-----------------|  
|[Elemento LanguagePack do VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obrigatórios. Fornece o elemento raiz para um pacote de idiomas do VSIX.|  
  
## <a name="text-value"></a>Valor de Texto  
 Opcional. Um link para um site da Web. O link é uma cadeia de texto.  
  
## <a name="element-information"></a>Informações sobre o elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Namespace    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Nome do Esquema   |                 Esquema do pacote de idiomas do VSIX                 |
| Arquivo de validação |                VSIXLanguagePackSchema.xsd                 |
|  Pode estar vazio   |                      Não aplicável                       |
  
## <a name="see-also"></a>Consulte Também  
 [Referência de esquema do pacote de idiomas VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizando pacotes VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referência do esquema de extensão do VSIX 1,0](/previous-versions/dd393700(v=vs.110))
