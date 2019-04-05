---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a29a8553a128903ed6da037f605a14bcb1db367c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924412"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera um nome amigável para o servidor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrName`  
 [out] Retorna um nome amigável para o servidor.  
  
> [!NOTE]
>  O chamador é responsável por liberar a cadeia de caracteres.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Para servidores iniciado pelo usuário, o nome retornado por esse método é o nome completo do servidor. Para servidores iniciado automaticamente, o nome é que, da máquina, o servidor está executando no.  
  
 Para um nome orientado por máquina, chame o [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
