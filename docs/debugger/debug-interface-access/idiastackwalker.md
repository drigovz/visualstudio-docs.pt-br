---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ad74f92765ee449eab1e3089511a063e70d96a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831927"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Fornece métodos para fazer uma pilha de percorrer usando as informações no arquivo. PDB.

## <a name="syntax"></a>Sintaxe

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
A tabela a seguir mostra os métodos de `IDiaStackWalker`.

|Método|Descrição|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera um enumerador de quadro de pilha para x86 de plataformas.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera um enumerador de quadro de pilha para um tipo de plataforma específica.|

## <a name="remarks"></a>Comentários
Essa interface é usada para obter uma lista de quadros de pilha para um módulo carregado. Cada um dos métodos é passada um [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (implementado pelo aplicativo cliente) de objeto que fornece as informações necessárias para criar a lista de quadros de pilha.

## <a name="notes-for-callers"></a>Observações para chamadores
Essa interface é obtida chamando o `CoCreateInstance` método com o identificador de classe `CLSID_DiaStackWalker` e a ID de interface do `IID_IDiaStackWalker`. O exemplo mostra como essa interface é obtida.

## <a name="example"></a>Exemplo
Este exemplo mostra como obter o `IDiaStackWalker` interface.

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Requisitos
Cabeçalho: Dia2.h

Biblioteca: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Consulte também
- [Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
