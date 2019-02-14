---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42ab689c5c94fcf0200775d9fdd59ac2a0f7202c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916971"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Retorna o bloco de dados PDATA associado com o endereço virtual.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `va`  
 [in] Especifica o endereço virtual dos dados a obter.  
  
 `cbData`  
 [in] O tamanho dos dados em bytes para obter.  
  
 `pcbData`  
 [out] Retorna o tamanho real dos dados em bytes, que foi obtido.  
  
 `pbData`  
 [no, out] Um buffer que será preenchido com os dados solicitados. Não pode ser `NULL`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhum PDATA para o endereço especificado. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 PDATA (a seção chamada ". pData") de um compiland contém informações sobre o tratamento de exceção para funções.  
  
 O chamador sabe a quantidade de dados deve ser retornado para que o chamador tenha nem precisa perguntar para a quantidade de dados está disponível. Portanto, é aceitável para a implementação desse método para retornar um erro se o `pbData` parâmetro é `NULL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)