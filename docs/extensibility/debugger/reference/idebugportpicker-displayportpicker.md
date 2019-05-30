---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 815b44735e36489991da84216e2fcc6db8e6fab4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308751"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Exibe a caixa de diálogo especificada que permite que o usuário seleciona uma porta.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Parâmetros
`hwndParentDialog`\
[in] Identificador para a caixa de diálogo pai.

`pbstrPortId`\
[out] Cadeia de caracteres de identificador de porta.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Um valor de retorno `S_FALSE` (ou um valor de retorno `S_OK` com o `BSTR` definido como `NULL`) indica que o usuário clicou **Cancelar**.

## <a name="see-also"></a>Consulte também
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)