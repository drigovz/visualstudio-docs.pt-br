---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724838"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Representa uma ui personalizada para selecionar a porta.

## <a name="syntax"></a>Sintaxe

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface é implementada por fornecedores portuários. Um fornecedor de porta define seu seletor de portas `metricPortPickerCLSID` expondo-o como clsid e apontando a métrica para o CLSID exposto.

## <a name="methods"></a>Métodos
 A tabela a seguir `IDebugPortPicker`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Exibe a caixa de diálogo especificada que permite ao usuário selecionar uma porta.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Define o provedor de serviços.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
