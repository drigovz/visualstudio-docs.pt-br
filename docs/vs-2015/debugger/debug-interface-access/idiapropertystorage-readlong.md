---
title: 'IDiaPropertyStorage:: ReadLONG | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08661272bea779ff0789619d58bf6f2837a21917
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538306"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lê `LONG` valores em um conjunto de propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `id`  
 no Identificador da propriedade a ser lida ( `PROPID` definida em WTypes. h como um `ULONG` ).  
  
 `pValue`  
 fora Retorna o valor da propriedade.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. Retorna `E_INVALIDARG` se a propriedade não é do tipo `LONG` .  
  
## <a name="remarks"></a>Comentários  
 Um `LONG` é definido pelo Windows como um inteiro com sinal de 32 bits.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
