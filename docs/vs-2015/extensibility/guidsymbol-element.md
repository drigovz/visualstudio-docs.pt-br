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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204216"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O `GuidSymbol` elemento contém o GUID do par GUID: ID que representa um menu, grupo ou comando. A ID vem de um `IDSymbol` elemento no `GuidSymbol` elemento. O `GuidSymbol` elemento tem um `name` atributo que fornece um nome amigável para o GUID, que está contido no `value` atributo.  
  
## <a name="syntax"></a>Syntax  
  
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
|name|Obrigatórios. Nome do símbolo de GUID.|  
|value|Obrigatórios. GUID do símbolo GUID.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contém a ID do par GUID: ID que representa um menu, grupo ou comando.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Symbols](../extensibility/symbols-element.md)|Agrupa `GuidSymbol` elementos em um arquivo. vsct.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, um arquivo. vsct contém três `GuidSymbol` elementos em sua `Symbols` seção, um para o pacote em si, um para o conjunto de comandos (a coleção de menus, grupos e comandos disponibilizados pelo pacote) e outro para os bitmaps que fornecem ícones para botões e outros componentes visuais. Cada `IDSymbol` elemento em um determinado `GuidSymbol` elemento deve ter um exclusivo `value` . No entanto, os `IDSymbol` elementos que têm valores idênticos podem existir em um pacote, desde que tenham diferentes pais.  
  
## <a name="see-also"></a>Consulte Também  
 [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
