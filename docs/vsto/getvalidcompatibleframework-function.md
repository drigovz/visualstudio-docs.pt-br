---
title: Função GetValidCompatibleFramework
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b93e0de5f1d8c1d4e93189e7bfee36d44db19319
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648872"
---
# <a name="getvalidcompatibleframework-function"></a>Função GetValidCompatibleFramework
  Essa API dá suporte à infraestrutura do Office e não se destina a ser usado diretamente do seu código.  

## <a name="syntax"></a>Sintaxe  

```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  

### <a name="parameters"></a>Parâmetros  

|Parâmetro|Descrição|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Não use.|  
|*pbstrValidFrameworkTag*|Não use.|  

## <a name="return-value"></a>Valor retornado  
 Se a função obtiver êxito, retorna **S_OK**. Se a função falhar, ele retornará um código de erro.  

