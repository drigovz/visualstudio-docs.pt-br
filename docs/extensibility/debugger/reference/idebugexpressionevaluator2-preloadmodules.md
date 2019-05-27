---
title: IDebugExpressionEvaluator2::PreloadModules | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::PreloadModules
- PreloadModules
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 154089f95c3a1aa14198923e45a2d44b532d1ac3
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211751"
---
# <a name="idebugexpressionevaluator2preloadmodules"></a>IDebugExpressionEvaluator2::PreloadModules
Pré-carrega os módulos designados pelo provedor do símbolo especificado.

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
[in] Provedor de símbolos para o qual os módulos serão pré-carregadas.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Esse método opcional é usado quando você fizer uma anexação de processo de hospedagem. Ele dá o EE uma chance para 'aquecimento' como parte do attach.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um **ExpressionEvaluatorPackage** objeto que expõe a [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interface.

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

## <a name="see-also"></a>Consulte também
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
