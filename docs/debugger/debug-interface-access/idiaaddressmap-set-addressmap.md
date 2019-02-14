---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3150cc591c77d1ab3abc31ed9b07062d094d3d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973090"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Fornece um mapa de endereço para dar suporte a traduções de layout da imagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cbData`  
 [in] O número de elementos no `data` parâmetro.  
  
 `data[]`  
 [in] Uma matriz de [estrutura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) estruturas que definem o mapa de conversão.  
  
 `imagetoSymbols`  
 [in] `TRUE` se o `data` parâmetro define um mapa do novo layout de imagem ao layout original (conforme descrito pelos símbolos de depuração). `FALSE` Se `data` é um mapa para o novo layout da imagem tirado o layout original.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, o DIA recupera mapas de tradução de endereço do arquivo de banco de dados (. PDB) do programa. Se esses valores estiverem ausentes, o [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) método é chamado duas vezes, uma vez com o `imagetoSymbols` parâmetro definido como `TRUE` e uma vez com o `imagetoSymbols` parâmetro definido como `FALSE`. Conversões de mapa de endereço não podem ser habilitados usando o [idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) método, a menos que ambos os mapas de tradução são fornecidos.  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)