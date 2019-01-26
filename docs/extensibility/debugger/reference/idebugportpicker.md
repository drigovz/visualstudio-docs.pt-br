---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 753303ecc5a3b3f66fe8135a5955308c0cf4e586
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957582"
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