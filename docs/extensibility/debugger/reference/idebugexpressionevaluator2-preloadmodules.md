---
title: IDebugExpressionEvaluator2::P reloadModules | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::PreloadModules
- PreloadModules
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db345fb2936ef7278675407549798ae669487f06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729323"
---
# <a name="idebugexpressionevaluator2preloadmodules"></a>IDebugExpressionEvaluator2::PreloadModules
Sobrecarrega os módulos designados pelo provedor de símbolos especificado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT PreloadModules (
    IDebugSymbolProvider* pSym
);
```

```csharp
int PreloadModules (
    IDebugSymbolProvider pSym
);
```

## <a name="parameters"></a>Parâmetros
`pSym`\
no O provedor de símbolos para o qual os módulos serão pré-carregados.

## <a name="return-value"></a>Valor Retornado
Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Esse método opcional é usado quando você faz uma anexação de processo de hospedagem. Ele dá ao EE a oportunidade de ' ficar quente ' como parte da anexação.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um objeto **ExpressionEvaluatorPackage** que expõe a interface [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) .

```cpp
STDMETHODIMP ExpressionEvaluatorPackage::PreloadModules
(
    IDebugSymbolProvider *pSym
)
{
    HRESULT hr = NOERROR;
    RuntimeMemberDescriptor  * prtMemberDesc;
    RuntimeClassDescriptor *prtClassDesc;
    CComPtr<IDebugClassField> pClassField;
    IfFalseGo(pSym,E_INVALIDARG);

    prtMemberDesc = &(g_rgRTLangMembers[StandardModuleAttributeCtor]);
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);

    pClassField = NULL;
    prtMemberDesc = &(g_rgRTLangMembers[LoadAssembly]);
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);

Error:
    return hr;
}
```

## <a name="see-also"></a>Confira também
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
