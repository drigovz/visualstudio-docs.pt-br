---
title: IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24e89d8a96ff1d615c75ae45b6846d7c3aedbf95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855637"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Chamado quando um arquivo Candidate. pdb é aberto.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT NotifyOpenPDB ( 
   LPCOLESTR pdbPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>Parâmetros
 `pdbPath`

no O caminho completo do arquivo. pdb.

 `resultCode`

no Código que indica o êxito ( `S_OK` ) ou a falha da carga, conforme aplicado a esse arquivo.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. O código de retorno é normalmente ignorado.

## <a name="see-also"></a>Consulte também
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)