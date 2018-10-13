---
title: 'Idialinenumber:: Get_addresssection | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_addressSection method
ms.assetid: a01c1bae-04b2-4c30-8621-60939a3124c2
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cc8503e9ca19d836fc6d60c7e5ae05a4a5b3925
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298955"
---
# <a name="idialinenumbergetaddresssection"></a>IDiaLineNumber::get_addressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera a parte da seção do endereço de memória em que um bloco é iniciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pRetVal  
 [out] Retorna a parte da seção do endereço de memória em que um bloco é iniciada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="example"></a>Exemplo  
  
```cpp#  
CComPtr< IDiaLineNumber > pLine;  
DWORD seg;  
pLine->get_addressSection( &seg );  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaLineNumber::get_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)



