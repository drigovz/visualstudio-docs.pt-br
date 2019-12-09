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
ms.openlocfilehash: b2bcf657b4404ed72059351175d124a9c07abb46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744946"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Prepara os dados de depuração armazenados em um arquivo de banco de dados do programa (. pdb) acessado por meio de um fluxo de dados na memória.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>Parâmetros
 pIStream

no Um objeto <xref:IStream> que representa o fluxo de dados a ser usado.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores de retorno para esse método.

|Valor|Descrição|
|-----------|-----------------|
|E_PDB_FORMAT|Tentativa de acessar um arquivo com um formato obsoleto.|
|E_INVALIDARG|Parâmetro inválido.|
|E_UNEXPECTED|A fonte de dados já foi preparada.|

## <a name="remarks"></a>Comentários
 Esse método permite que os dados de depuração de um executável sejam obtidos da memória por meio de um objeto <xref:IStream>.

 Para carregar um arquivo. pdb sem validação, use o método [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

 Para validar o arquivo. pdb em relação a critérios específicos, use o método [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

 Para obter acesso ao processo de carregamento de dados (por meio de um mecanismo de retorno de chamada), use o método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Consulte também
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)