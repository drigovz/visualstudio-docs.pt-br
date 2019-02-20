---
title: IDiaImageData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData interface
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 625b9dd6a1ffb6e982097626018617c9b74d4746
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227100"
---
# <a name="idiaimagedata"></a>IDiaImageData
Expõe os detalhes da base deslocamentos da memória e o local do módulo ou da imagem.

## <a name="syntax"></a>Sintaxe

```
IDiaImageData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
A tabela a seguir mostra os métodos de `IDiaImageData`.

|Método|Descrição|
|------------|-----------------|
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Recupera o local na memória virtual do módulo relativo para o aplicativo.|
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Recupera o local na memória virtual da imagem.|
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Recupera o local da memória onde a imagem deve ser baseada.|

## <a name="remarks"></a>Comentários
Alguns fluxos de depuração (XDATA, PDATA) contêm cópias dos dados também é armazenados na imagem. Eles transmitem dados de objetos podem ser consultados quanto a `IDiaImageData` interface. Consulte a seção "Observações para chamadores" neste tópico para obter detalhes.

## <a name="notes-for-callers"></a>Observações para chamadores
Obtenha essa interface chamando `QueryInterface` em um [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) objeto. Observe que nem todos depurar fluxos de suporte a `IDiaImageData` interface. Por exemplo, no momento, somente os fluxos XDATA e PDATA dão suporte a `IDiaImageData` interface.

## <a name="example"></a>Exemplo
Este exemplo pesquisa todos os fluxos de depuração para qualquer fluxo que dá suporte a `IDiaImageData` interface. Se tal fluxo for encontrado, algumas informações sobre esse fluxo são exibidas.

```C++
void ShowImageData(IDiaSession *pSession)
{
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumDebugStreams> pStreamsList;
        HRESULT hr;

        hr = pSession->getEnumDebugStreams(&pStreamsList);
        if (SUCCEEDED(hr))
        {
            LONG numStreams = 0;
            hr = pStreamsList->get_Count(&numStreams);
            if (SUCCEEDED(hr))
            {
                ULONG fetched = 0;
                for (LONG i = 0; i < numStreams; i++)
                {
                    CComPtr<IDiaEnumDebugStreamData> pStream;
                    hr = pStreamsList->Next(1,&pStream,&fetched);
                    if (fetched == 1)
                    {
                        CComPtr<IDiaImageData> pImageData;
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),
                                                     (void **)&pImageData);
                        if (SUCCEEDED(hr))
                        {
                            CComBSTR name;
                            hr = pStream->get_name(&name);
                            if (SUCCEEDED(hr))
                            {
                                wprintf(L"Stream %s:\n",(BSTR)name);
                            }
                            else
                            {
                                wprintf(L"Failed to get name of stream\n");
                            }

                            ULONGLONG imageBase = 0;
                            if (pImageData->get_imageBase(&imageBase) == S_OK)
                            {
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);
                            }

                            DWORD relVA = 0;
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)
                            {
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);
                            }

                            ULONGLONG va = 0;
                            if (pImageData->get_virtualAddress(&va) == S_OK)
                            {
                                wprintf(L"  virtual address = 0x%0I64x\n", va);
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
Cabeçalho: Dia2.h

Biblioteca: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Consulte também
[Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
