---
title: 'IDebugSettingsCallback2:: GetEEMetricGuid | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1cf70c424856b93eb4d082a167bc671b885a346
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155185"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera o identificador exclusivo para uma métrica do avaliador de expressão Considerando seu nome.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetEEMetricGuid(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   GUID*   pguidValue  
);  
```  
  
```csharp  
HRESULT GetEEMetricGuid(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out Guid pguidValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidLang`  
 no Identificador exclusivo da linguagem de programação.  
  
 `guidVendor`  
 no Identificador exclusivo do fornecedor.  
  
 `pszMetric`  
 no Nome da métrica.  
  
 `pguidValue`  
 fora Retorna o identificador exclusivo da métrica.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
