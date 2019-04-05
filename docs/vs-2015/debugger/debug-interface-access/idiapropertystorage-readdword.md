---
title: IDiaPropertyStorage::ReadDWORD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e92b74fc1165adf359614e354ab60f3fc118e34b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923108"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lê `DWORD` valores em um conjunto de propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
