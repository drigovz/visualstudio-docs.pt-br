---
title: Função EnsureVSTOComponent
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 88ed4de9f126f819f0cbdc7f3f49b4798ccb2195
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838957"
---
# <a name="ensurevstocomponent-function"></a>Função EnsureVSTOComponent
  Essa API dá suporte à infraestrutura do Office e não se destina a ser usado diretamente do seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|*pProject*|Não use.|  
  
## <a name="return-value"></a>Valor retornado  
 Se a função obtiver êxito, retorna **S_OK**. Se a função falhar, ele retornará um código de erro.  
