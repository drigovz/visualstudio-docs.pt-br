---
title: IDiaDataSource::loadDataFromIStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb9b218935085b04ae1a9931733aeca34766aa5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833680"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Prepara os dados de depuração armazenados em um arquivo de banco de dados (. PDB) do programa acessado por meio de um fluxo de dados na memória.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>Parâmetros
 pIStream

[in] Um <xref:IStream> objeto que representa o fluxo de dados a ser usado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores retornados para esse método.

|Valor|Descrição|
|-----------|-----------------|
|E_PDB_FORMAT|Tentativa de acessar um arquivo com um formato obsoleto.|
|E_INVALIDARG|Parâmetro inválido.|
|E_UNEXPECTED|Fonte de dados já foi preparada.|

## <a name="remarks"></a>Comentários
 Esse método permite que os dados de depuração para um executável a ser obtida da memória por meio de um <xref:IStream> objeto.

 Para carregar um arquivo. PDB sem validação, use o [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) método.

 Para validar o arquivo. PDB em relação a critérios específicos, use o [idiadatasource:: Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) método.

 Para obter acesso para o processo de carregamento de dados (por meio de um mecanismo de retorno de chamada), use o [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.

## <a name="see-also"></a>Consulte também
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)