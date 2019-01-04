---
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a503ff99542215ba5922feb860fc04cd047ce287
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869668"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Estende os tipos de campos que estão disponíveis para oferecer suporte a genéricos de código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>Métodos  
 Além dos métodos na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Recupera o tipo de campo estendidas especificado.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Determina se o campo representa um tipo fechado.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll