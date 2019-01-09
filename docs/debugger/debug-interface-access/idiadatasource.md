---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 837372903dd1435c9cc5603805a85ce608481fc9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904251"
---
# <a name="idiadatasource"></a>IDiaDataSource
Inicia o acesso a uma fonte de símbolos de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaDataSource`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera o nome do arquivo para o último erro de carregamento.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Abre e prepara um arquivo de banco de dados (. PDB) do programa como uma fonte de dados de depuração.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Abre e verifica se o arquivo de banco de dados (. PDB) de programa corresponde as informações de assinatura fornecidas; prepara o arquivo. PDB como uma fonte de dados de depuração.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Abre e prepara os dados de depuração associados ao arquivo.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara os dados de depuração armazenados em um arquivo de banco de dados (. PDB) do programa acessado por meio de um fluxo de dados na memória.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Abre uma sessão para consultar os símbolos.|  
  
## <a name="remarks"></a>Comentários  
 Uma chamada para um dos métodos de carga a `IDiaDataSource` interface abrirá a fonte de símbolo. Uma chamada bem-sucedida para o [idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md) método retorna um [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interface que dá suporte à consulta de fonte de dados. Se o método load retorna um erro relacionado ao arquivo o [idiadatasource:: Get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) valor contém o nome do arquivo associado ao erro de retorno do método.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é obtida chamando o `CoCreateInstance` função com o identificador de classe `CLSID_DiaSource` e a ID de interface do `IID_IDiaDataSource`. O exemplo mostra como essa interface é obtida.  
  
## <a name="example"></a>Exemplo  
  
```C++  
  
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
 Cabeçalho: dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)