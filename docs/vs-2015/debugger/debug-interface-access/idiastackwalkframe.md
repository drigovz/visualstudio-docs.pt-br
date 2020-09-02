---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150144"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mantém o contexto de pilha entre invocações do método [IDiaFrameData:: execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalkFrame : IUnknown  
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
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces (debug interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
