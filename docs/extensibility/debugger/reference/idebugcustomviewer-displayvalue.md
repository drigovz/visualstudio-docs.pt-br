---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732447"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Este método é chamado para exibir o valor especificado.

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

## <a name="parameters"></a>parâmetros
`hwnd`\
[em] Janela dos pais

`dwID`\
[em] ID para espectadores personalizados que suportam mais de um tipo.

`pHostServices`\
[in] Reservado. Sempre definido como nulo.

`pDebugProperty`\
[em] Interface que pode ser usada para recuperar o valor a ser exibido.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro.

## <a name="remarks"></a>Comentários
 O visor é "modal" na forma de que este método criará a janela necessária, exibirá o valor, aguardará a entrada e fechará a janela, tudo antes de retornar ao chamador. Isso significa que o método deve lidar com todos os aspectos da exibição do valor da propriedade, desde a criação de uma janela para saída, até a espera pela entrada do usuário, até a destruição da janela.

 Para suportar a alteração do valor no objeto [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dado, você pode usar o método [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) — se o valor puder ser expresso como uma seqüência de string. Caso contrário, é necessário criar uma interface personalizada — exclusiva `DisplayValue` do avaliador de expressão que `IDebugProperty3` implementa esse método — no mesmo objeto que implementa a interface. Esta interface personalizada forneceria métodos para alterar os dados de um tamanho ou complexidade arbitrária.

## <a name="see-also"></a>Confira também
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
