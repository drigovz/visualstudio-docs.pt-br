---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05db065b047629e1eaac49e5f6aeeb05eed4307e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863819"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Mantém o contexto de pilha entre invocações do método [IDiaFrameData:: execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .

## <a name="syntax"></a>Sintaxe

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IDiaStackWalkFrame` .

|Método|Descrição|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Recupera o valor de um registro.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Define o valor de um registro.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Lê a memória da imagem.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Pesquisa o quadro de pilha especificado para o endereço de retorno de função mais próximo.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Pesquisa o quadro de ativação especificado em busca de um endereço de retorno no endereço especificado ou próximo dele.|

## <a name="remarks"></a>Comentários
 Essa interface é usada durante a execução do programa para ler e gravar registros, bem como para acessar a memória e localizar endereços de retorno.

## <a name="notes-for-callers"></a>Observações para chamadores
 O aplicativo cliente implementa essa interface e passa uma instância da interface para o método [IDiaFrameData:: execute](../../debugger/debug-interface-access/idiaframedata-execute.md) . A mesma instância dessa interface é usada novamente e novamente para manter o estado dos registros durante cada invocação do `execute` método. O `execute` método também usa essa interface para determinar o endereço de retorno.

## <a name="requirements"></a>Requisitos
 Cabeçalho: dia2. h

 Biblioteca: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Consulte também
- [Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)