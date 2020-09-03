---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a02eb9048c0e9338e6300fc63666af4db535b3ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198586"
---
# <a name="idiadatasource"></a>IDiaDataSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Inicia o acesso a uma fonte de símbolos de depuração.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDiaDataSource` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera o nome do arquivo para o último erro de carregamento.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Abre e prepara um arquivo de banco de dados do programa (. pdb) como uma fonte de dado de depuração.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Abre e verifica se o arquivo de banco de dados do programa (. pdb) corresponde às informações de assinatura fornecidas; Prepara o arquivo. pdb como uma fonte de dados de depuração.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Abre e prepara os dados de depuração associados ao arquivo. exe/. dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara os dados de depuração armazenados em um arquivo de banco de dados do programa (. pdb) acessado por meio de um fluxo de dados na memória.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Abre uma sessão para consultar símbolos.|  
  
## <a name="remarks"></a>Comentários  
 Uma chamada para um dos métodos Load da `IDiaDataSource` interface abre a origem do símbolo. Uma chamada bem-sucedida para o método [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) retorna uma interface [IDiaSession](../../debugger/debug-interface-access/idiasession.md) que dá suporte à consulta à fonte de dados. Se o método Load retornar um erro relacionado a arquivo, o valor de retorno do método [IDiaDataSource:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) conterá o nome do arquivo associado ao erro.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é obtida chamando-se a `CoCreateInstance` função com o identificador de classe `CLSID_DiaSource` e a ID de interface de `IID_IDiaDataSource` . O exemplo mostra como essa interface é obtida.  
  
## <a name="example"></a>Exemplo  
  
```cpp#  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
