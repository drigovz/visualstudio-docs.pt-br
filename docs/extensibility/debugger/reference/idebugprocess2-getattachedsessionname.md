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
ms.openlocfilehash: aa932817c796249803558ad1eb877f620198b3e4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703533"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Obtém o nome da sessão que está sendo depurado neste processo. Um IDE pode exibir essas informações para um usuário que estiver depurando um processo específico em um computador específico.

> [!NOTE]
>  Esse método é preterido e sua implementação deve retornar sempre `E_NOTIMPL`.

## <a name="syntax"></a>Sintaxe

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

#### <a name="parameters"></a>Parâmetros
 `pbstrSessionName`

## <a name="return-value"></a>Valor de retorno
 Esse método deve retornar sempre `E_NOTIMPL`.

## <a name="see-also"></a>Consulte também
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)