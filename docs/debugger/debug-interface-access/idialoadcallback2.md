---
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d58a109c3eb63bd3a1f59fb0009ba01809eca1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855623"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Recebe retornos de chamada do procedimento de localização de símbolo de DIA, permitindo que as restrições sejam impostas no processo de localização.

## <a name="syntax"></a>Sintaxe

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Além dos métodos na interface [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) , essa interface expõe os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Determina se está procurando um arquivo. pdb no diretório de depuração original.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Determina se é permitido procurar um arquivo. pdb no caminho em que o arquivo. exe está localizado.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Determina se procurar informações de depuração é permitida a partir de arquivos. dbg.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Determina se a pesquisa de arquivos. pdb é permitida no diretório raiz do sistema.|

## <a name="remarks"></a>Comentários
 O aplicativo cliente implementa essa interface e fornece uma referência a ela na chamada para o método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) . Lembre-se de implementar todos os métodos na interface [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) também.

## <a name="requirements"></a>Requisitos
 Cabeçalho: dia2. h

 Biblioteca: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Consulte também
- [Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)