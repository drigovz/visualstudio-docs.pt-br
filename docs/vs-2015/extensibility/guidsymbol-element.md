---
title: Elemento GuidSymbol | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924541"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O `GuidSymbol` elemento contém o GUID do par GUID:ID que representa um menu, um grupo ou um comando. A ID vem de uma `IDSymbol` elemento no `GuidSymbol` elemento. O `GuidSymbol` elemento tem um `name` que fornece um nome amigável para o GUID, que está contido no atributo o `value` atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Necessário. Nome do símbolo GUID.|  
|Valor |Necessário. GUID do símbolo GUID.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contém a ID do par GUID:ID que representa um menu, um grupo ou um comando.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Symbols](../extensibility/symbols-element.md)|Grupos de `GuidSymbol` elementos em um arquivo. VSCT.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, um arquivo. VSCT contém três `GuidSymbol` elementos no seu `Symbols` seção, um para o pacote propriamente dito, um para o conjunto de comandos (a coleção de menus, grupos e comandos que disponibiliza o pacote) e para os bitmaps que fornecem ícones de botões e outros componentes do visual. Cada `IDSymbol` elemento em um determinado `GuidSymbol` elemento deve ter um único `value`. No entanto, `IDSymbol` elementos que têm valores idênticos podem existir em um pacote, desde que eles tenham pais diferentes.  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
