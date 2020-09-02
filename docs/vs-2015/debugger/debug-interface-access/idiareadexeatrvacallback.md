---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8275756a4b89ab56148a9f7b560eda5d671fc6a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150582"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Permite que um aplicativo cliente forneça bytes de um arquivo executável, conforme especificado por um endereço virtual relativo.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDiaReadExeAtRVACallback` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Lê o número especificado de bytes começando no endereço virtual relativo (RVA) especificado do arquivo executável.|  
  
## <a name="remarks"></a>Comentários  
 O aplicativo cliente implementa essa interface para fornecer os bytes do executável usando um endereço virtual relativo no arquivo do executável. Para usar um deslocamento de arquivo absoluto, implemente a interface [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Esse método é implementado pelo aplicativo cliente e passado para o método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) como um método alternativo para ler o arquivo.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces (debug interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
