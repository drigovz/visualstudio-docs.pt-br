---
title: 'Idiainjectedsource:: Get_source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a923e323f4ca9dc7f661457add7665f8c136ae92
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824451"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Recupera os bytes de código de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cbData`  
 [in] O número de bytes que representa o tamanho do buffer de dados.  
  
 `pcbData`  
 [out] Retorna o número de bytes que representa os bytes retornados. Se `data` está `NULL`, em seguida, `pcbData` é o número total de bytes de dados disponíveis.  
  
 `data[]`  
 [out] Um buffer que deve ser preenchida com os bytes de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)