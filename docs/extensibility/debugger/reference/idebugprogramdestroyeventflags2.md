---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1b131679a287fb555fcf2a78a803c77457d47ca
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343506"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permite que um mecanismo de depuração substituir o comportamento padrão do [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário quando você encerrar uma sessão de depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Essa interface é implementada pelos mecanismos de depuração. É útil para hosts que podem criar e destruir vários programas durante a vida útil de um processo.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugProgramDestroyEventFlags2`.

|Método|Descrição|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera o programa destruir sinalizadores.|

## <a name="remarks"></a>Comentários
 O comportamento padrão do [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário é retornar ao modo de design depois que todos os programas tem enviado um programa destruir o evento. Essa interface permite que um mecanismo de depuração alterar esse comportamento.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll