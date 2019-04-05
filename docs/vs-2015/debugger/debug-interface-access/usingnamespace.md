---
title: UsingNameSpace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- UsingNamespace symbol tag
ms.assetid: e8e1beb5-7cb9-43b4-9ff4-760d5f91ea2d
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e5be853d75fd1aa7ed701c428cdb15822d867cc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926697"
---
# <a name="usingnamespace"></a>UsingNameSpace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Alguns símbolos pode ser referenciados por namespace e subsequentemente seria identificados por um `SymTagUsingNameSpace` marca.  
  
> [!NOTE]
>  A marca de símbolo UsingNamespace aparece apenas em código gerenciado.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir mostra as propriedades que são válidas para esse tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo para o delimitador compiland, bloco ou função.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID do símbolo léxico pai.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome do namespace.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice de símbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retorna `SymTagNameSpace` (um dos [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valores).|  
  
## <a name="see-also"></a>Consulte também  
 [Hierarquia lexical de tipos de símbolo](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
