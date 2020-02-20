---
title: Elemento License (esquema do pacote de idiomas do VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1299d97cbda78049732d3367a9231272397e2ec
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477071"
---
# <a name="license-element-vsix-language-pack-schema"></a>Elemento License (esquema do pacote de idiomas do VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcional. O caminho de uma versão localizada do arquivo de licença para a extensão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<License>FilePath\license.txt</License>  
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
 O caminho relativo do arquivo de licença localizado a ser exibido.  
  
## <a name="remarks"></a>Comentários  
 Se o elemento `License` for definido, o texto do arquivo de licença designado será exibido durante a instalação e o usuário deverá aceitar a licença para continuar.  
  
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
