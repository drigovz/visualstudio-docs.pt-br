---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8dd4f85bfdfb58baff3301c2d858f52933f16d1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958590"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Representa uma interface do usuário personalizada para selecionar a porta.

## <a name="syntax"></a>Sintaxe

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada por fornecedores de porta. Um fornecedor de porta define seu seletor de porta expondo-o como um CLSID e apontando a `metricPortPickerCLSID` métrica no CLSID exposto.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugPortPicker` .

|Método|Descrição|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Exibe a caixa de diálogo especificada que permite ao usuário selecionar uma porta.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Define o provedor de serviços.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
