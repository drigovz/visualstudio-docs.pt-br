---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c40a2da886b4e999649349d4af306295c87863ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916071"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Representa as informações do servidor de origem que estão contidas em um arquivo PDB.

## <a name="syntax"></a>Sintaxe

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Essa interface é implementada por mecanismos de depuração e consumida pelo depurador da interface do usuário.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugSourceServerModule`.

|Método|Descrição|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera uma matriz de informações do servidor de origem.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll