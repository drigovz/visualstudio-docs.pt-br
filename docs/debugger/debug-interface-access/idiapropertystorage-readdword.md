---
title: IDiaPropertyStorage::ReadDWORD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed37f7f8126f5477fb63304ea6b6248cba190679
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828271"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Lê `DWORD` valores em um conjunto de propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `id`  
 [in] Identificador da propriedade a ser lido (`PROPID` é definido em wtypes. H como um `ULONG`).  
  
 `pValue`  
 [out] Retorna o valor da propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará um código de erro. Retorna `E_INVALIDARG` se a propriedade não é do tipo `DWORD`.  
  
## <a name="remarks"></a>Comentários  
 Um `DWORD` é definido pelo Windows como um inteiro sem sinal de 32 bits.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)