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
ms.openlocfilehash: 7492e0eee0523fd102ecd057d075f2672bf3b25b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695837"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Recupera correspondente de nomes de cadeia de caracteres para receber identificadores de propriedade.

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

[in] Número de ids de propriedade no `rgpropid`.

 `rgpropid`

[in] Matriz de ids de propriedade para o qual obter os nomes (`PROPID` é definido em wtypes. H como um `ULONG`).

 `rglpwstrName`

[no, out] Matriz de nomes de propriedade para as ids de propriedade especificada. A matriz deve ser pré-alocada para suportar o número solicitado de nomes de propriedade e deve ser capaz de armazenar pelo menos `cpropid``BSTR` cadeias de caracteres.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Os nomes de propriedade retornada devem ser liberados (chamando o `SysFreeString` função) quando eles não são mais necessários.

## <a name="see-also"></a>Consulte também
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)