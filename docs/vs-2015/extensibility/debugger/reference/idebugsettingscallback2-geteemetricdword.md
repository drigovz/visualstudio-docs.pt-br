---
title: IDebugSettingsCallback2::GetEEMetricDword | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8223676dc534461e86b15bfa3c6344095ce2accd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897381"
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera um valor que corresponde à métrica do avaliador de expressão especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetEEMetricDword(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```csharp  
private int GetEEMetricDword(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidLang`  
 [in] Identificador exclusivo da linguagem de programação.  
  
 `guidVendor`  
 [in] Identificador exclusivo do fornecedor.  
  
 `pszMetric`  
 [in] Nome da métrica.  
  
 `pdwValue`  
 [out] Retorna o valor que corresponde à cadeia de métrica.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

