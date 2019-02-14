---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6a190cecdfbf9d7ae77543d8a955a52a3f16d15
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070624"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Permite que um aplicativo cliente para fornecer os bytes de um arquivo executável, conforme especificado por um endereço virtual relativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaReadExeAtRVACallback`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Lê o número especificado de bytes começando no especificado endereço virtual relativo (RVA) do arquivo executável.|  
  
## <a name="remarks"></a>Comentários  
 O aplicativo cliente implementa essa interface para fornecer os bytes do executável usando um endereço virtual relativo ao arquivo do executável. Para usar um deslocamento de arquivo absoluto, implementar o [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Esse método é implementado pelo aplicativo cliente e passado para o [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método como um método alternativo para ler o arquivo.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)