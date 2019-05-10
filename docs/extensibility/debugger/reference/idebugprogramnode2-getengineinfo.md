---
title: IDebugProgramNode2::GetEngineInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c31d3a858af2886a27a51e22e131cb89b2234d6e
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65459078"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Obtém o nome e o identificador do mecanismo de depuração (DES) executando um programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>Parâmetros
 `pbstrEngine`\

 [out] Retorna o nome do DE execução do programa (C++-específico: isso pode ser um ponteiro nulo, indicando que o chamador não está interessado no nome do mecanismo de).

 `pguidEngine`\

 [out] Retorna o identificador global exclusivo do DE execução do programa (C++-específico: isso pode ser um ponteiro nulo, indicando que o chamador não está interessado no GUID do mecanismo de).

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)