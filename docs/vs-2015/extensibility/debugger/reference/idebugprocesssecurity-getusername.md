---
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202780"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o nome de usuário do fornecedor da porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrUserName`  
 fora Uma cadeia de caracteres que contém o nome de usuário.  
  
## <a name="return-value"></a>Valor Retornado  
 Se o método for bem-sucedido, retornará `S_OK`. Caso contrário, ele retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 `GetUserName` Retorna o nome de usuário exibido na coluna **nome de usuário** da caixa de diálogo **anexar ao processo** . Para exibir a caixa de diálogo **anexar ao processo** , clique em **anexar ao processo** no menu **ferramentas** no [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE).  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
