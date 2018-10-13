---
title: IDiaEnumTables | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45156a7a7c69c59a3b9ad53ca4d8f9afc4bf814a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200415"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enumera as várias tabelas contidas na fonte de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaEnumTables : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaEnumTables`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Recupera o [IEnumVARIANT Interface](http://msdn.microsoft.com/en-us/139e3c93-faef-4003-9079-e0e94494db3e) versão este enumerador.|  
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Recupera o número de tabelas.|  
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Recupera uma tabela por meio de um índice ou um nome.|  
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Recupera um número especificado de tabelas na sequência de enumeração.|  
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Ignora um número especificado de tabelas em uma sequência de enumeração.|  
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Obtenha essa interface por meio da chamada a [idiasession:: Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) método.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como obter o `IDiaEnumTables` interface de uma sessão. Para obter um exemplo mais completo de como usar tabelas, consulte a [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interface.  
  
```cpp#  
void ShowTableNames(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    // Do something with table  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de acesso à Interface de depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)



