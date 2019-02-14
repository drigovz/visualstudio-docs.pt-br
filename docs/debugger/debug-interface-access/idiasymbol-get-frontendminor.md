---
title: IDiaSymbol::get_frontEndMinor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc74214dfdad676926c20a83d74c4ee9016fc200
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965962"
---
# <a name="idiasymbolgetfrontendminor"></a>IDiaSymbol::get_frontEndMinor
Recupera o número de versão secundária do front-end.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna o número de versão secundária front.end.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, um compilador é composto de dois elementos principais: o front-end (Analisador), que manipula a análise de código-fonte em um formulário intermediário, e um back-end (gerador de código), que converte o formulário intermediário em assembly. Não é incomum para o front-end ter uma versão diferente do back-end.  
  
 Um front-end ou um número de versão de back-end é composto de três partes: \<principal >.\< secundária >. \<compilar >, onde \<principais > é o número de versão principal \<secundária > é o número de versão secundária, e \<compilar > é o número de compilação. Por exemplo, 13.10.3077.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descrição|  
|-----------------|-----------------|  
|Cabeçalho:|dia2.h|  
|Versão:|DIA SDK v7.0|  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)