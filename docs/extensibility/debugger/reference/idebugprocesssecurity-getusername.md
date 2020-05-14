---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723252"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtém o nome de usuário do fornecedor do porto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>parâmetros
`pbstrUserName`\
[fora] Uma seqüência contendo o nome de usuário.

## <a name="return-value"></a>Valor retornado
 Se o método for bem-sucedido, retornará `S_OK`. Caso contrário, ele retorna um código de erro.

## <a name="remarks"></a>Comentários
 `GetUserName`retorna o nome de usuário exibido na coluna Nome de **usuário** da caixa de diálogo **Anexar ao processo.** Para exibir a caixa de diálogo **Anexar ao processo,** [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] clique em Anexar ao **processo** no menu **Ferramentas** no ambiente de desenvolvimento integrado (IDE).

## <a name="see-also"></a>Confira também
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
