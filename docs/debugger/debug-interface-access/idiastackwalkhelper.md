---
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80f269df947227f36e0c87a7efeddda8d8ef1248
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944222"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Facilita a movimentar a pilha usando o arquivo de banco de dados (. PDB) de depuração do programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de VTable  
 A tabela a seguir mostra os métodos de `IDiaStackWalkHelper`:  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Recupera o valor de um registro.|  
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Define o valor de um registro.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Lê um bloco de dados de imagem do arquivo executável na memória.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Pesquisa o quadro de pilha especificada para o endereço de retorno de função mais próximo.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Pesquisa o quadro de pilha especificada para um endereço de retorno em ou próximo o endereço de pilha especificada.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Recupera o registro de ativação que contém o endereço virtual especificado.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Recupera o símbolo que contém o endereço virtual especificado. **Observação:**  Símbolo deve ter o tipo `SymTagFunctionType` (um valor a partir de [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração).|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Retorna o bloco de dados PDATA associado com o endereço virtual especificado.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Recupera o endereço virtual inicial de um executável, dado um endereço virtual em algum lugar no espaço de memória do executável.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é chamada pelo código do DIA para obter informações sobre o executável para construir uma lista de quadros de pilha durante a execução do programa.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Um aplicativo cliente implementa essa interface para dar suporte a movimentar a pilha durante a execução do programa. Uma instância dessa interface é passada para o [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) ou [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)