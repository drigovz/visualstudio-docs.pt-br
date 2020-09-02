---
title: IDiaSectionContrib::get_comdat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddf479a2da74803916b7afc1945eb610d6b0e668
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576627"
---
# <a name="idiasectioncontribget_comdat"></a>IDiaSectionContrib::get_comdat
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera um sinalizador que indica se a seção é um registro COMDAT.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_comdat (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna `TRUE` se a seção é um registro COMDAT; caso contrário, retorna `FALSE` .  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um registro COMDAT é um registro COFF (formato de arquivo de objeto comum) que torna as funções empacotadas visíveis para o vinculador.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
