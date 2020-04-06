---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0a02169b37bba804034990ed5d972f973244769
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724896"
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

## <a name="parameters"></a>parâmetros
`hwndParentDialog`\
[em] Manuseie a caixa de diálogo pai.

`pbstrPortId`\
[fora] Seqüência de identificador de porta.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Um valor `S_FALSE` de retorno de `S_OK` (ou `BSTR` um `NULL`valor de retorno de com o conjunto para ) indica que o usuário clicou **em Cancelar**.

## <a name="see-also"></a>Confira também
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
