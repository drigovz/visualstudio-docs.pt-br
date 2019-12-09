---
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743087"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Chamado quando um diretório de depuração foi encontrado no arquivo. exe.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Parâmetros
 `fExecutable`

[in] `TRUE` se o diretório de depuração for lido a partir de um executável (em vez de um arquivo. dbg).

 `cbData`

no Contagem de bytes de dados no diretório de depuração.

 `data[]`

no Uma matriz que é preenchida com o diretório de depuração.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. O código de retorno é normalmente ignorado.

## <a name="remarks"></a>Comentários
 O método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) invoca esse retorno de chamada quando ele encontra um diretório de depuração durante o processamento do arquivo executável.

 Esse método remove a necessidade do cliente de fazer a engenharia reversa do arquivo executável e/ou de depuração para dar suporte a informações de depuração diferentes das encontradas no arquivo. pdb. Com esses dados, o cliente pode reconhecer o tipo de informações de depuração disponíveis e se ele reside no arquivo executável ou no arquivo. dbg.

 A maioria dos clientes não precisará desse retorno de chamada, pois o método `IDiaDataSource::loadDataForExe` abre de forma transparente os arquivos. PDB e. dbg quando necessário para atender aos símbolos.

## <a name="see-also"></a>Consulte também
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)