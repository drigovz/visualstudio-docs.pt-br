---
title: 'IDebugProgram2:: getdebugproperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b86a1aa144e553b126445a865330a8edb786ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187911"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém as propriedades do programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppProperty`  
 fora Retorna um objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa as propriedades do programa.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As propriedades retornadas por esse método são específicas para o programa. Se o programa precisar retornar mais de uma propriedade, o objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) retornado por esse método será um contêiner de propriedades adicionais e chamar o método [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) retornará uma lista de todas as propriedades.  
  
 Um programa pode expor qualquer número e tipo de propriedades adicionais que podem ser descritas por meio da `IDebugProperty2` interface. Um IDE pode exibir as propriedades de programa adicionais por meio de uma interface de usuário do navegador de propriedades genérico.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
