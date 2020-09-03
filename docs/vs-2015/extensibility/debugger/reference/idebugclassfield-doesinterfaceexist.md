---
title: IDebugClassField::D oesInterfaceExist | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f71346c1b69729ae54ef0d33be4149e7000316c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191133"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se uma interface específica está definida na classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszInterfaceName`  
 no Uma cadeia de caracteres que contém o nome da interface a ser procurada.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK, retornará S_FALSE se a interface não existir; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método em vigor Obtém uma enumeração de todas as interfaces e procura uma interface correspondente na lista.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
