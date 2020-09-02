---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537349"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera os nomes de cadeia de caracteres correspondentes para determinados identificadores de propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cpropid`  
 no Número de IDs de propriedade no `rgpropid` .  
  
 `rgpropid`  
 no Matriz de IDs de propriedade para as quais obter os nomes ( `PROPID` é definido em WTypes. h como um `ULONG` ).  
  
 `rglpwstrName`  
 [entrada, saída] Matriz de nomes de propriedade para as IDs de propriedade especificadas. A matriz deve ser pré-configurada para conter o número solicitado de nomes de propriedade e deve ser capaz de armazenar pelo menos `cpropid``BSTR` cadeias de caracteres.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Os nomes de propriedade retornados devem ser liberados (chamando a `SysFreeString` função) quando não forem mais necessários.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
