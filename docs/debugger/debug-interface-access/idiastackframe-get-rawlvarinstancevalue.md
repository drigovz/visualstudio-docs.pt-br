---
title: IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741631"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Esse método recupera o valor da variável local especificada como bytes brutos.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>Parâmetros
 `pInstance`

no Um objeto `IDiaLVarInstance` que representa uma instância da variável local para obter o valor.

 `cbDataMax`

no Número máximo de bytes no buffer apontados por `pbData`. Pode ser um máximo de 8 bytes (`sizeof(ULONGLONG)`).

 `pcbData`

fora Retorna o número real de bytes armazenados no buffer.

 `pbData`

fora Um buffer a ser preenchido com dados. Esse não pode ser `NULL`.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)