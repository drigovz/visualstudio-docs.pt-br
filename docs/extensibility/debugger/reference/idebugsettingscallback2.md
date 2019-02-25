---
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3dea6edb6045e21931651ff5c20a01a5f000ff62
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722675"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Habilita mecanismos para ler configurações de métrica de depuração remotamente.

## <a name="syntax"></a>Sintaxe

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
Essa interface é implementada pelo retorno de chamada de evento do Gerenciador de sessão de depuração e consumida por mecanismos de depuração. Ele também pode ser usado localmente em vez de. lib de Dbgmetric [d].

## <a name="methods"></a>Métodos
A tabela a seguir mostra os métodos de `IDebugSettingsCallback2`.

|Método|Descrição|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Enumera os avaliadores de expressão disponível considerando os identificadores de idioma e o fornecedor.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Recupera um objeto local de avaliador de expressão dado a métrica.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Recupera um valor que corresponde à métrica do avaliador de expressão especificada.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Recupera o arquivo métrica de avaliador de expressão considerando o nome ou a métrica.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Recupera o identificador exclusivo para uma métrica de avaliador de expressão dado seu nome.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Recupera a cadeia de caracteres do valor de uma métrica de avaliador de expressão dada seu nome.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Recupera o valor de uma métrica, dado seu nome.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Recupera o identificador exclusivo de uma métrica, dado seu nome.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Recupera a cadeia de caracteres do valor da métrica dada seu nome.|

## <a name="requirements"></a>Requisitos
Cabeçalho: Msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma função que usa um **IDebugSettingsCallback2** objeto como um parâmetro.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
