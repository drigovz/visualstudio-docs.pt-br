---
title: IDiaPropertyStorage::Enum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fd383270dabc0117434badf50f48af6f4e695a3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966207"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Obtém um enumerador para as propriedades nesse conjunto.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppenum`  
 [out] Retorna um `IEnumSTATPROPSTG` objeto (no namespace Microsoft.VisualStudio.OLE.Interop) que representa uma enumeração de propriedades.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)