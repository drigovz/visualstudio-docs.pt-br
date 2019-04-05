---
title: IDiaDataSource::loadDataFromIStream | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35644f06ae929e4168d5dc44d6fc488de020a637
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58923308"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prepara os dados de depuração armazenados em um arquivo de banco de dados (. PDB) do programa acessado por meio de um fluxo de dados na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
