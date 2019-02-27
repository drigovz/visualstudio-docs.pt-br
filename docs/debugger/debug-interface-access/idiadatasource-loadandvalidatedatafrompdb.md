---
title: IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5426e27d7b100c42cd571935b1634d6dbd6e990f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626135"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Abre e verifica se o arquivo de banco de dados (. PDB) de programa corresponde as informações de assinatura fornecidas e prepara o arquivo. PDB como uma fonte de dados de depuração.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT loadAndValidateDataFromPdb ( 
   LPCOLESTR pdbPath,
   GUID*     pcsig70,
   DWORD     sig,
   DWORD     age
);
```

#### <a name="parameters"></a>Parâmetros
`pdbPath`

[in] O caminho para o arquivo. PDB.

`pcsig70`

[in] A assinatura GUID para verificar em relação à assinatura do arquivo. PDB. Arquivos apenas. PDB [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e versões posteriores possuem assinaturas GUID.

`sig`

[in] A assinatura de 32 bits para verificar em relação à assinatura do arquivo. PDB.

`age`

[in] Valor de idade para verificar. A idade não necessariamente corresponde a qualquer valor de tempo conhecido, ele é usado para determinar se um arquivo. PDB está fora de sincronia com um arquivo .exe correspondente.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores retornados para esse método.

|Valor|Descrição|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Falha ao abrir o arquivo ou o arquivo tem um formato inválido.|
|E_PDB_FORMAT|Tentativa de acessar um arquivo com um formato obsoleto.|
|E_PDB_INVALID_SIG|Assinatura não corresponde.|
|E_PDB_INVALID_AGE|Não corresponde a idade.|
|E_INVALIDARG|Parâmetro inválido.|
|E_UNEXPECTED|A fonte de dados já foi preparada.|

## <a name="remarks"></a>Comentários
Um arquivo. PDB contém valores de assinatura e idade. Esses valores são replicados no arquivo. dll ou. .exe que corresponde ao arquivo. PDB. Antes de preparar a fonte de dados, esse método verifica a assinatura e a idade do arquivo. PDB chamado coincidir com os valores fornecidos.

Para carregar um arquivo. PDB sem validação, use o [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) método.

Para obter acesso para o processo de carregamento de dados (por meio de um mecanismo de retorno de chamada), use o [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.

Para carregar um arquivo. PDB diretamente da memória, use o [idiadatasource:: Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) método.

## <a name="example"></a>Exemplo

```C++
IDiaDataSource* pSource;  // Previously created data source.
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);
DWORD expectedFileSignature = 0x12345678;
DWORD expectedAge           = 128;

HRESULT hr;
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",
                                          &expectedGUIDSignature,
                                          expectedFileSignature,
                                          expectedAge);
if (FAILED(hr))
{
    // Report an error
}

```

## <a name="see-also"></a>Consulte também
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
