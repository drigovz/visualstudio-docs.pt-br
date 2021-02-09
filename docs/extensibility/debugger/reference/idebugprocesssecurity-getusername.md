---
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 075cc96866a2b7b4a987c04c6cb78dcd22da2b50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912025"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtém o nome de usuário do fornecedor da porta.

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

## <a name="parameters"></a>Parâmetros
`pbstrUserName`\
fora Uma cadeia de caracteres que contém o nome de usuário.

## <a name="return-value"></a>Valor retornado
 Se o método for bem-sucedido, retornará `S_OK`. Caso contrário, ele retorna um código de erro.

## <a name="remarks"></a>Comentários
 `GetUserName` Retorna o nome de usuário exibido na coluna **nome de usuário** da caixa de diálogo **anexar ao processo** . Para exibir a caixa de diálogo **anexar ao processo** , clique em **anexar ao processo** no menu **ferramentas** no [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE).

## <a name="see-also"></a>Confira também
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
