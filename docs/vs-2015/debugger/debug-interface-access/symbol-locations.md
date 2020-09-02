---
title: Locais de símbolo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1f9ea0c6f2eede11100a4956ef4c63b20c6fa9a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193560"
---
# <a name="symbol-locations"></a>Locais de símbolos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A maioria dos símbolos tem um local definido dentro do arquivo de imagem. O local de um símbolo é especificado com um valor da enumeração de [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md) . O símbolo pode dar suporte a propriedades adicionais, dependendo de sua localização.  
  
 A tabela a seguir mostra os tipos de local usados com mais frequência e suas propriedades adicionais.  
  
|Tipo de local|Propriedades adicionais|  
|-------------------|---------------------------|  
|`LocIsNull`|nenhum|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol:: get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (se os endereços virtuais relativos estiverem habilitados)<br /><br /> [IDiaSymbol:: get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (se a base da imagem tiver sido definida como diferente de zero)|  
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|  
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSymbol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [IDiaSymbol:: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSymbol:: get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [IDiaSymbol:: get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [IDiaSymbol:: get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [IDiaSymbol:: get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [IDiaSymbol:: get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [IDiaSymbol:: get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [IDiaSymbol:: get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [IDiaSymbol:: get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [IDiaSymbol:: get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Símbolos e marcações de símbolos](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
