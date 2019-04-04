---
title: IDiaLoadCallback2::RestrictSystemRootAccess | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4a603936f58df37cd54bc32e7b4ea8e35838aa7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58921793"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Determina se a procura de arquivos. PDB é permitido no diretório raiz do sistema.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT RestrictSystemRootAccess();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Qualquer código de retorno diferente de `S_OK` impede que pesquisa a raiz do sistema de arquivos. PDB.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
