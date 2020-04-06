---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722495"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Habilita um mecanismo de depuração para [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] substituir o comportamento padrão da ia quando você termina uma sessão de depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface é implementada por motores de depuração. É útil para hosts que podem criar e destruir vários programas ao longo da vida de um processo.

## <a name="methods"></a>Métodos
 A tabela a seguir `IDebugProgramDestroyEventFlags2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera o programa de destruir bandeiras.|

## <a name="remarks"></a>Comentários
 O comportamento padrão [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] da ui é voltar ao modo de design depois de todos os programas terem enviado um evento de destruição de programa. Esta interface permite que um mecanismo de depuração altere esse comportamento.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
