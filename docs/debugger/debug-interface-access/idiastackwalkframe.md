---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 343c56e3d3175c26900b0cfb4cdc3d816a324404
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630581"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Mantém o contexto de pilha entre invocações da [idiaframedata:: execute](../../debugger/debug-interface-access/idiaframedata-execute.md) método.

## <a name="syntax"></a>Sintaxe

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDiaStackWalkFrame`.

|Método|Descrição|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Recupera o valor de um registro.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Define o valor de um registro.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Lê a memória da imagem.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Pesquisa o quadro de pilha especificada para o endereço de retorno de função mais próximo.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Pesquisa o quadro de pilha especificada para um endereço de retorno em ou próximo o endereço especificado.|

## <a name="remarks"></a>Comentários
 Essa interface é usada durante a execução do programa para ler e gravar registros, bem como acessar a memória e localizar endereços de retornados.

## <a name="notes-for-callers"></a>Observações para chamadores
 O aplicativo cliente implementa essa interface e passa uma instância da interface para o [idiaframedata:: execute](../../debugger/debug-interface-access/idiaframedata-execute.md) método. A mesma instância dessa interface é usada várias vezes para manter o estado dos registros durante cada chamada a `execute` método. O `execute` método também usa essa interface para determinar o endereço de retorno.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Dia2.h

 Biblioteca: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Consulte também
- [Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)