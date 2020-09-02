---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150086"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Retorna o bloco de dados PDATA associado ao endereço virtual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `va`  
 no Especifica o endereço virtual dos dados a serem obtidos.  
  
 `cbData`  
 no O tamanho dos dados em bytes a serem obtidos.  
  
 `pcbData`  
 fora Retorna o tamanho real dos dados em bytes que foram obtidos.  
  
 `pbData`  
 [entrada, saída] Um buffer que é preenchido com os dados solicitados. Não pode ser `NULL`.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhum pData para o endereço especificado. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O PDATA (a seção denominada ". pData") de um compiland contém informações sobre a manipulação de exceção para funções.  
  
 O chamador sabe a quantidade de dados a ser retornada para que o chamador não precise solicitar a quantidade de dados disponível. Portanto, é aceitável que uma implementação desse método retorne um erro se o `pbData` parâmetro for `NULL` .  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
