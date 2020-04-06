---
title: IDebugSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11e180288a9312d9af5a3d3b1bd63d8f2266f581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719175"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
Esta interface representa um provedor de símbolos que fornece símbolos e tipos, devolvendo-os como campos.

## <a name="syntax"></a>Sintaxe

```
IDebugSymbolProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
Um provedor de símbolos deve implementar essa interface para fornecer informações de símbolo e tipo a um avaliador de expressão.

## <a name="notes-for-callers"></a>Observações para chamadores
Essa interface é obtida usando `CoCreateInstance` a função do COM (para provedores de símbolos não gerenciados) ou carregando o conjunto de código gerenciado apropriado e instanciando o provedor de símbolos com base nas informações encontradas nesse conjunto. O mecanismo de depuração instancia o provedor de símbolos para trabalhar em coordenação com o avaliador de expressão. Consulte o Exemplo para uma abordagem para instanciar esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
A tabela a seguir `IDebugSymbolProvider`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|`Initialize`|Preterido. Não use.|
|`Uninitialize`|Preterido. Não use.|
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Obtém o campo que contém o endereço de depuração.|
|`GetField`|Preterido. Não use.|
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|Mapeia uma posição de documento em uma matriz de endereços de depuração.|
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Mapeia um contexto de documento em uma matriz de endereços de depuração.|
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Mapeia um endereço de depuração em um contexto de documento.|
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Obtém o idioma usado para compilar o código no endereço de depuração.|
|`GetGlobalContainer`|Preterido. Não use.|
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|Obtém o campo representando um nome de método totalmente qualificado.|
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Obtém o tipo de campo de classe representando um nome de classe totalmente qualificado.|
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Cria um enumerador para namespaces associados ao endereço de depuração.|
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Mapeia um nome de símbolo para um tipo de símbolo.|
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|Obtém o endereço de depuração que segue um endereço de depuração dado em um método.|

## <a name="remarks"></a>Comentários
Esta interface mapeia posições de documentos em endereços de depuração e vice-versa.

## <a name="requirements"></a>Requisitos
Cabeçalho: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemplo
Este exemplo mostra como instanciar o provedor de símbolos, dado o seu GUID (um mecanismo de depuração deve saber esse valor).

```cpp
// A debug engine uses its own symbol provider and would know the GUID
// of that provider.
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugSymbolProvider *pProvider = NULL;
    if (pSymbolProviderGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetSPMetric(*pSymbolProviderGuid,
                      storetypeFile,
                      metricCLSID,
                      &clsidProvider,
                      strRegistrationRoot);
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {
            // No file type provider, try metadata provider.
            ::GetSPMetric(*pSymbolProviderGuid,
                          ::storetypeMetadata,
                          metricCLSID,
                          &clsidProvider,
                          strRegistrationRoot);
        }
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugSymbolProvider> spSymbolProvider;
            spSymbolProvider.CoCreateInstance(clsidProvider);
            if (spSymbolProvider != NULL) {
                pProvider = spSymbolProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
