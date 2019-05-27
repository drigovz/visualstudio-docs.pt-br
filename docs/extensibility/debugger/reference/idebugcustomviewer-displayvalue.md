---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c374cfa79b91d70895f94be4f1c3f28c5ac4c02
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205167"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Esse método é chamado para exibir o valor especificado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Parâmetros
`hwnd`\
[in] Janela pai

`dwID`\
[in] ID para visualizadores personalizados que dão suporte a mais de um tipo.

`pHostServices`\
[in] Reservado. Sempre definido como null.

`pDebugProperty`\
[in] Interface que pode ser usado para recuperar o valor a ser exibido.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.

## <a name="remarks"></a>Comentários
 A exibição é "modal" em que esse método criar a janela necessária, exibir o valor, aguarda a entrada e fechar a janela, todos antes de retornar ao chamador. Isso significa que o método deve tratar todos os aspectos de exibir o valor da propriedade, desde a criação de uma janela de saída, para aguardar entrada do usuário, a destruição de janela.

 Para dar suporte à alteração do valor na determinada [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) objeto, você pode usar o [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) método — se o valor pode ser expresso como uma cadeia de caracteres. Caso contrário, será necessário criar uma interface personalizada — exclusiva para o avaliador de expressão implementar isso `DisplayValue` método — no mesmo objeto que implementa o `IDebugProperty3` interface. Essa interface personalizada fornece métodos para alterar os dados de um tamanho arbitrário ou complexidade.

## <a name="see-also"></a>Consulte também
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)