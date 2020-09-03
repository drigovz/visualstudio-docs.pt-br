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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722495"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permite que um mecanismo de depuração substitua o comportamento padrão da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário quando você finaliza uma sessão de depuração.

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada pelos mecanismos de depuração. É útil para hosts que podem criar e destruir vários programas durante o tempo de vida de um processo.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugProgramDestroyEventFlags2` .

|Método|Descrição|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera os sinalizadores de destruição do programa.|

## <a name="remarks"></a>Comentários
 O comportamento padrão da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário é voltar para o modo de design depois que todos os programas tiverem enviado um evento de destruição de programa. Essa interface permite que um mecanismo de depuração altere esse comportamento.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
