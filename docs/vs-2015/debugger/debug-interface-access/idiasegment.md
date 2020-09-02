---
title: IDiaSegment | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fe9586797c334afb60f60311963dc2df72fdad5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151731"
---
# <a name="idiasegment"></a>IDiaSegment
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mapeia dados do número da seção para segmentos de espaço de endereço.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSegment : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDiaSegment` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Recupera o número do segmento.|  
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Recupera o deslocamento em segmentos em que a seção começa.|  
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Recupera o número de bytes no segmento.|  
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Recupera um sinalizador que indica se o segmento pode ser lido.|  
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Recupera um sinalizador que indica se o segmento pode ser modificado.|  
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Recupera um sinalizador que indica se o segmento é executável.|  
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Recupera o número da seção que é mapeado para este segmento.|  
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Recupera o endereço virtual relativo (RVA) do início da seção.|  
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Recupera o endereço virtual (VA) do início da seção.|  
  
## <a name="remarks"></a>Comentários  
 Como o DIA SDK já executa traduções da seção deslocamento para endereços virtuais relativos, a maioria dos aplicativos não fará uso das informações no mapa de segmentos.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Obtenha essa interface chamando os métodos [IDiaEnumSegments:: item](../../debugger/debug-interface-access/idiaenumsegments-item.md) ou [IDiaEnumSegments:: Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) . Consulte o exemplo para obter detalhes.  
  
## <a name="example"></a>Exemplo  
 Essa função exibe o endereço de todos os segmentos em uma tabela e o símbolo mais próximo.  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSegments ),  
                               (void**)&pSegments )  
                  )  
       )  
    {  
        CComPtr<IDiaSegment> pSegment;  
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&  
                celt == 1 )  
        {  
            DWORD rva;  
            DWORD seg;  
  
            pSegment->get_addressSection( &seg );  
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )  
            {  
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );  
                pSegment = NULL;  
  
                CComPtr<IDiaSymbol> pSym;  
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
                {  
                    CDiaBSTR name;  
                    DWORD    tag;  
  
                    pSym->get_symTag( &tag );  
                    pSym->get_name( &name );  
                    printf( "\tClosest symbol: %ws (%ws)\n",  
                            name != NULL ? name : L"",  
                            szTags[ tag ] );  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces (debug interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSegments:: item](../../debugger/debug-interface-access/idiaenumsegments-item.md)   
 [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
