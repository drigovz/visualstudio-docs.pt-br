---
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edfcb7d1603160c2f857508c3dd32ce0696b6d7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352985"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Representa uma soma de verificação de documento para uma solicitação de ponto de interrupção.

## <a name="syntax"></a>Sintaxe

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Implementado pela [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurar pacote e consumido por mecanismos de depuração.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugBreakpointChecksumRequest2`.

|Método|Descrição|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Recupera a soma de verificação de documento para uma solicitação de ponto de interrupção recebe o identificador exclusivo do algoritmo de soma de verificação para usar.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Determina se a soma de verificação está habilitada para este documento.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll