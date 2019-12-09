---
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09b4c04b996d180f1975ee1e9ad3a9a95cd1b76a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337458"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Permite que um mecanismo de depuração que usa DCOM para perguntar a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário para certificar-se de que o firewall não bloqueará a depuração remota.

## <a name="syntax"></a>Sintaxe

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Implementado pelo objeto de porta do Gerenciador de sessão de depuração.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugFirewallConfigurationCallback2`.

|Método|Descrição|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Solicita que o firewall não bloqueie a depuração remota.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll