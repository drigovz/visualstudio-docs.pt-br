---
title: 'IDebugProgramNode2:: GetEngineInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3e24c2c326f7ebc7427da3804f17f1f75aeef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205738"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o nome e o identificador do mecanismo de depuração (DE) que executa um programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrEngine`  
 fora Retorna o nome da execução do programa (específico do C++: esse pode ser um ponteiro nulo indicando que o chamador não está interessado no nome do mecanismo).  
  
 `pguidEngine`  
 fora Retorna o identificador global exclusivo da execução do programa (específico do C++: esse pode ser um ponteiro nulo indicando que o chamador não está interessado no GUID do mecanismo).  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
