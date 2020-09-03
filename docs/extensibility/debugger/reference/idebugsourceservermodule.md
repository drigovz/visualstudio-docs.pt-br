---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719916"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Representa as informações do servidor de origem contidas em um arquivo PDB.

## <a name="syntax"></a>Syntax

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada pelos mecanismos do depurador e consumida pela interface do usuário do depurador.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugSourceServerModule` .

|Método|Descrição|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera uma matriz de informações do servidor de origem.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
