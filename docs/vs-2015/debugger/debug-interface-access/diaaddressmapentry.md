---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67c0a3e297f3eebfbf44724e64c4989d9bb979fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164350"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Descreve uma entrada em um mapa de endereços.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Elementos  
 `rva`  
 Um RVA (endereço virtual relativo) na imagem A.  
  
 `rvaTo`  
 O endereço virtual relativo `rva` é mapeado para a imagem B.  
  
## <a name="remarks"></a>Comentários  
 Um mapa de endereços fornece uma tradução de um layout de imagem (A) para outro (B). Uma matriz de `DiaAddressMapEntry` estruturas classificada por `rva` define um mapa de endereços.  
  
 Para converter um endereço, `addrA` , na imagem a para um endereço, `addrB` , na imagem B, execute as seguintes etapas:  
  
1. Pesquise o mapa para a entrada, `e` , com o maior `rva` menor ou igual a `addrA` .  
  
2. Defina `delta = addrA – e.rva`.  
  
3. Defina `addrB = e.rvaTo + delta`.  
  
   Uma matriz de `DiaAddressMapEntry` estruturas é passada para o método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dia2. h  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
