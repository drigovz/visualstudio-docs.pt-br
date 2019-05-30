---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a42b67eb3fd308011bf725f8dd7e24a4d9ddca6f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311517"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtém o nome de usuário do fornecedor de porta.

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
[out] Uma cadeia de caracteres que contém o nome de usuário.

## <a name="return-value"></a>Valor de retorno
 Se o método for bem-sucedido, ele retornará `S_OK`. Caso contrário, ele retornará um código de erro.

## <a name="remarks"></a>Comentários
 `GetUserName` Retorna o nome de usuário que é exibido na **nome de usuário** coluna o **anexar ao processo** caixa de diálogo. Para exibir o **anexar ao processo** caixa de diálogo, clique em **anexar ao processo** no **ferramentas** menu no [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE).

## <a name="see-also"></a>Consulte também
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)