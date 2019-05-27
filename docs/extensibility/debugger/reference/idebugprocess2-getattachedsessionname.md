---
title: IDebugProcess2::GetAttachedSessionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84a0969eb93fc2e95449364521662c27bf6f750d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202649"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Obtém o nome da sessão que está sendo depurado neste processo. Um IDE pode exibir essas informações para um usuário que estiver depurando um processo específico em um computador específico.

> [!NOTE]
> Esse método é preterido e sua implementação deve retornar sempre `E_NOTIMPL`.

## <a name="syntax"></a>Sintaxe

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parâmetros
`pbstrSessionName`\

## <a name="return-value"></a>Valor de retorno
 Esse método deve retornar sempre `E_NOTIMPL`.

## <a name="see-also"></a>Consulte também
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)