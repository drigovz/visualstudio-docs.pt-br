---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742864"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Recupera os nomes de cadeia de caracteres correspondentes para determinados identificadores de propriedade.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>Parâmetros
 `cpropid`

no Número de IDs de propriedade no `rgpropid`.

 `rgpropid`

no Matriz de IDs de propriedade para as quais obter os nomes (`PROPID` é definido em WTypes. h como um `ULONG`).

 `rglpwstrName`

[entrada, saída] Matriz de nomes de propriedade para as IDs de propriedade especificadas. A matriz deve ser pré-configurada para conter o número solicitado de nomes de propriedade e deve ser capaz de armazenar pelo menos `cpropid``BSTR` cadeias de caracteres.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Os nomes de propriedade retornados devem ser liberados (chamando a função `SysFreeString`) quando não forem mais necessários.

## <a name="see-also"></a>Consulte também
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)