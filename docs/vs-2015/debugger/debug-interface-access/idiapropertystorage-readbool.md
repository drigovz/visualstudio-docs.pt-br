---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64eee421a5ed5bd46a64b51694d913a4f2dc4d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538870"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lê `BOOL` valores em um conjunto de propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `id`  
 no Identificador da propriedade a ser lida ( `PROPID` definida em WTypes. h como um `ULONG` ).  
  
 `pValue`  
 fora Retorna o valor da propriedade.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. Retorna `E_INVALIDARG` se a propriedade não é do tipo `BOOL` .  
  
## <a name="remarks"></a>Comentários  
 Para obter resultados consistentes, interprete o `BOOL` valor de forma que os valores diferentes de `TRUE` zero sejam `FALSE` .  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
