---
title: IDiaLoadCallback::RestrictRegistryAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25e6397b65c717be65a9a707dd0a53fc70321acb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828485"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
Determina se as consultas de registro podem ser usadas para localizar caminhos de pesquisa do símbolo.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Qualquer código de retorno diferente de `S_OK` impede que consultar o registro para caminhos de pesquisa do símbolo.

## <a name="see-also"></a>Consulte também
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)