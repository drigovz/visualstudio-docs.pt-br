---
title: CustomType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CustomType symbol
ms.assetid: 1b66bc0a-7979-416f-bf7f-e5df91584c91
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5caaceecdd2d88622c5922e4d40a9a8829bf7f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164412"
---
# <a name="customtype"></a>CustomType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tipos definidos pelo fornecedor (tipos específicos do compilador) são identificados por um `SymTagCustomType` símbolo.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir mostra as propriedades válidas adicionais para esse tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|`DWORD`|Identificador do OEM.|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|`DWORD`|ID interna do OEM.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID do índice do símbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retorna `SymTagCustomType` (um dos valores de [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|O primeiro tipo referenciado pelo símbolo de tipo personalizado.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID do símbolo de tipo.|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|`IDiaSymbol**`|Matriz de todos os tipos referenciados pelo símbolo de tipo personalizado.|  
  
## <a name="see-also"></a>Consulte Também  
 [Hierarquia de classes de tipos de símbolo](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
