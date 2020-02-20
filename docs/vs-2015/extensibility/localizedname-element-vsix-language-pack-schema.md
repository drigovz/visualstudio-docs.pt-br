---
title: Elemento localizadaname (esquema do pacote de idiomas do VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58e491290122a9d525ff8129333ac0f52ac5f778
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477032"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Elemento localizadaname (esquema do pacote de idiomas do VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obrigatórios. O nome localizado da extensão a ser instalada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Name>Localized name of the extension</Name>  
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
 Obrigatórios. O nome do pacote de idiomas no idioma de destino.  
  
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
