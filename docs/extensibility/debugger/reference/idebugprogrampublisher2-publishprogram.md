---
title: IDebugProgramPublisher2::PublishProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1553070f9afecf6ce60ac51b94ecb3f05d0eb9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698762"
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Esse método faz um programa disponível para mecanismos de depuração (DEs) e o Gerenciador de sessão de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT PublishProgram(
   CONST_GUID_ARRAY Engines,
   LPCOLESTR        szFriendlyName,
   IUnknown*        pDebuggeeInterface
);
```

```csharp
int PublishProgram(
   CONST_GUID_ARRAY Engines,
   string           szFriendlyName,
   object           pDebuggeeInterface
);
```

#### <a name="parameters"></a>Parâmetros
 `Engines`

 [in] Uma matriz de GUIDs para DEs que pode iniciar ou anexar a este programa.

 `szFriendlyName`

 [in] Nome amigável para o programa (isso aparece nos menus ou caixas de diálogo apresentadas ao usuário).

 `pDebuggeeInterface`

 [in] `IUnknown` interface para o programa (esse valor é usado como um cookie para identificar exclusivamente o programa; esse mesmo valor é usado para "Cancelar a publicação" o programa)

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Para criar um programa não está mais disponível para depuração, chame [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).

## <a name="see-also"></a>Consulte também
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)