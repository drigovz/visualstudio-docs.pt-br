---
title: IDiaDataSource::loadDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7526ba6e62c9df22a2338adc80f5d56578502cdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744935"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Abre e prepara um arquivo de banco de dados do programa (. pdb) como uma fonte de dado de depuração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parâmetros
pdbPath

no O caminho para o arquivo. pdb.

## <a name="return-value"></a>Valor retornado
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores de retorno para esse método.

|Valor|Descrição|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Falha ao abrir o arquivo ou foi determinado que o arquivo tem um formato inválido.|
|E_PDB_FORMAT|Tentativa de acessar um arquivo com um formato obsoleto.|
|E_INVALIDARG|Parâmetro inválido.|
|E_UNEXPECTED|A fonte de dados já foi preparada.|

## <a name="remarks"></a>Comentários
Esse método carrega os dados de depuração diretamente de um arquivo. pdb.

Para validar o arquivo. pdb em relação a critérios específicos, use o método [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Para obter acesso ao processo de carregamento de dados (por meio de um mecanismo de retorno de chamada), use o método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Para carregar um arquivo. pdb diretamente da memória, use o método [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Exemplo

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Consulte também
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
