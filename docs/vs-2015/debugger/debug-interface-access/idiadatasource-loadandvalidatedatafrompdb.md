---
title: IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f19a910af45ed70ae74c72441890ecae6c81d2a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198627"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre e verifica se o arquivo do banco de dados do programa (. pdb) corresponde às informações de assinatura fornecidas e prepara o arquivo. pdb como uma fonte de dado de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdbPath`  
 no O caminho para o arquivo. pdb.  
  
 `pcsig70`  
 no A assinatura de GUID a ser verificada em relação à assinatura do arquivo. pdb. Somente arquivos. pdb no [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] e posterior têm assinaturas de GUID.  
  
 `sig`  
 no A assinatura de 32 bits a ser verificada em relação à assinatura do arquivo. pdb.  
  
 `age`  
 no Valor de idade a ser verificado. A idade não corresponde necessariamente a nenhum valor de tempo conhecido, ela é usada para determinar se um arquivo. pdb está fora de sincronia com um arquivo. exe correspondente.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores de retorno para esse método.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Falha ao abrir o arquivo ou o arquivo tem um formato inválido.|  
|E_PDB_FORMAT|Tentativa de acessar um arquivo com um formato obsoleto.|  
|E_PDB_INVALID_SIG|A assinatura não corresponde.|  
|E_PDB_INVALID_AGE|A idade não corresponde.|  
|E_INVALIDARG|Parâmetro inválido.|  
|E_UNEXPECTED|A fonte de dados já foi preparada.|  
  
## <a name="remarks"></a>Comentários  
 Um arquivo. pdb contém valores de assinatura e idade. Esses valores são replicados no arquivo. exe ou. dll que corresponde ao arquivo. pdb. Antes de preparar a fonte de dados, esse método verifica se a assinatura do arquivo. pdb nomeada e a idade correspondem aos valores fornecidos.  
  
 Para carregar um arquivo. pdb sem validação, use o método [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Para obter acesso ao processo de carregamento de dados (por meio de um mecanismo de retorno de chamada), use o método [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
 Para carregar um arquivo. pdb diretamente da memória, use o método [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .  
  
## <a name="example"></a>Exemplo  
  
```cpp#  
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
  
## <a name="see-also"></a>Consulte Também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
