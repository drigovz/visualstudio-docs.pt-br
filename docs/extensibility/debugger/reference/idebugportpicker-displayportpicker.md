---
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49cc4500e887a3fbfcd8f6da8a62c42c75ef56aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929531"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Exibe a caixa de diálogo especificada que permite ao usuário selecionar uma porta.

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
no Identificador da caixa de diálogo pai.

`pbstrPortId`\
fora Cadeia de caracteres do identificador de porta.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. Um valor de retorno de `S_FALSE` (ou um valor de retorno de `S_OK` com o `BSTR` definido como `NULL` ) indica que o usuário clicou em **Cancelar**.

## <a name="see-also"></a>Confira também
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
