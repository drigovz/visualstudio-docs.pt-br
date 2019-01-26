---
title: Função GetValidCompatibleFramework
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 79b97867a3a5c87f1e208d93efacea711ba71efc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869301"
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
