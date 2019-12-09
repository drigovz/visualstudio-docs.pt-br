---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 991480886c2c43c330ce37561d383ffdc420e214
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340360"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Representa uma interface do usuário personalizada para selecionar a porta.

## <a name="syntax"></a>Sintaxe

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Essa interface é implementada por fornecedores de porta. Um fornecedor de porta define seu seletor de porta expô-lo como um CLSID e apontando a `metricPortPickerCLSID` métrica no CLSID exposto.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugPortPicker`.

|Método|Descrição|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Exibe a caixa de diálogo especificada que permite que o usuário seleciona uma porta.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Define o provedor de serviço.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll