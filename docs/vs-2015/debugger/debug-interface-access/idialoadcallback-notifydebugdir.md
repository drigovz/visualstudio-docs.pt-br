---
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e8fe8ffe9d7d495e40c8c84b08aeaefb03e8d17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152009"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Chamado quando um diretório de depuração foi encontrado no arquivo. exe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fExecutable`  
 [in] `TRUE` Se o diretório de depuração for lido a partir de um executável (em vez de um arquivo. dbg).  
  
 `cbData`  
 no Contagem de bytes de dados no diretório de depuração.  
  
 `data[]`  
 no Uma matriz que é preenchida com o diretório de depuração.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. O código de retorno é normalmente ignorado.  
  
## <a name="remarks"></a>Comentários  
 O método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) invoca esse retorno de chamada quando ele encontra um diretório de depuração durante o processamento do arquivo executável.  
  
 Esse método remove a necessidade do cliente de fazer a engenharia reversa do arquivo executável e/ou de depuração para dar suporte a informações de depuração diferentes das encontradas no arquivo. pdb. Com esses dados, o cliente pode reconhecer o tipo de informações de depuração disponíveis e se ele reside no arquivo executável ou no arquivo. dbg.  
  
 A maioria dos clientes não precisará desse retorno de chamada, pois o `IDiaDataSource::loadDataForExe` método abre de forma transparente os arquivos. PDB e. dbg quando necessário para atender aos símbolos.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
