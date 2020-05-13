---
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732421"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Essa interface permite que um avaliador de expressão (EE) exiba o valor de uma propriedade em qualquer formato necessário.

## <a name="syntax"></a>Sintaxe

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
Um EE implementa essa interface para exibir o valor de uma propriedade em um formato personalizado.

## <a name="notes-for-callers"></a>Observações para chamadores
Uma chamada para `CoCreateInstance` a função do COM instancia esta interface. O `CLSID` passe `CoCreateInstance` para é obtido no registro. Uma chamada para [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) obtém o local no registro. Consulte Observações para obter detalhes, bem como o Exemplo.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
Esta interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Faz o que for necessário para exibir um determinado valor.|

## <a name="remarks"></a>Comentários
Essa interface é usada quando o valor de uma propriedade não pode ser exibido por meios normais — por exemplo, com uma tabela de dados ou outro tipo de propriedade complexa. Um visualizador personalizado, `IDebugCustomViewer` representado pela interface, é diferente de um visualizador de tipo, que é um programa externo para exibir dados de um tipo específico, independentemente do EE. O EE implementa um visualizador personalizado que é específico para esse EE. Um usuário seleciona qual tipo de visualizador usar, seja um visualizador de tipo ou um visualizador personalizado. Consulte [Visualização e Visualização de Dados](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obter detalhes sobre este processo.

Um visualizador personalizado é registrado da mesma forma que um EE e, portanto, requer um GUID de idioma e um GUID de fornecedor. A métrica exata (ou nome de entrada de registro) é conhecida apenas pelo EE. Essa métrica é devolvida na estrutura [DEBUG_CUSTOM_VIEWER,](../../../extensibility/debugger/reference/debug-custom-viewer.md) que por sua vez é retornada por uma chamada para [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). O valor armazenado na `CLSID` métrica é o que `CoCreateInstance` é passado para a função do COM (veja o Exemplo).

Os ajudantes de sdk para `SetEEMetric`função [de depuração,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) podem ser usados para registrar um visualizador personalizado. Consulte a seção de registro `Debugging SDK Helpers` "Avaliadores de expressão" das chaves de registro específicas que um visualizador personalizado precisa. Observe que um visualizador personalizado precisa de apenas uma métrica (que é definida pelo implementador do EE), enquanto um avaliador de expressão requer várias métricas predefinidas.

Normalmente, um visualizador personalizado fornece uma exibição somente leitura dos dados, uma vez que a interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) fornecida ao [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) não tem métodos para alterar o valor da propriedade, exceto como uma string. Para suportar a alteração de blocos arbitrários de dados, o EE implementa uma interface personalizada no mesmo objeto que implementa a `IDebugProperty3` interface. Essa interface personalizada forneceria então os métodos necessários para alterar um bloco arbitrário de dados.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemplo
Este exemplo mostra como obter o primeiro visualizador personalizado de uma propriedade se essa propriedade tiver algum visualizador personalizado.

```cpp
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)
{
    // This string is typically defined globally.  For this example, it
    // is defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugCustomViewer *pViewer = NULL;
    if (pProperty != NULL) {
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);
        if (pProperty3 != NULL) {
            HRESULT hr;
            ULONG viewerCount = 0;
            hr = pProperty3->GetCustomViewerCount(&viewerCount);
            if (viewerCount > 0) {
                ULONG viewersFetched = 0;
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };
                hr = pProperty3->GetCustomViewerList(0,
                                                     1,
                                                     &viewerInfo,
                                                     &viewersFetched);
                if (viewersFetched == 1) {
                    CLSID clsidViewer = { 0 };
                    CComPtr<IDebugCustomViewer> spCustomViewer;
                    // Get the viewer's CLSID from the registry.
                    ::GetEEMetric(viewerInfo.guidLang,
                                  viewerInfo.guidVendor,
                                  viewerInfo.bstrMetric,
                                  &clsidViewer,
                                  strRegistrationRoot);
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {
                        // Instantiate the custom viewer.
                        spCustomViewer.CoCreateInstance(clsidViewer);
                        if (spCustomViewer != NULL) {
                            pViewer = spCustomViewer.Detach();
                        }
                    }
                }
            }
        }
    }
    return(pViewer);
}
```

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
