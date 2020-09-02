---
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4042cf58ee34b5f49df601b94e1110f03e0b6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197561"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Executa o desenrolamento de pilha e retorna os resultados em uma interface de quadro de movimentação de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `frame`  
 no Um objeto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) que contém o estado dos registros de quadro.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores de retorno para esse método.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Não é possível executar um registro de ativação no código de prólogo.|  
|E_DIA_SYNTAX|Erro de análise encontrado no programa de quadro.|  
|E_DIA_FRAME_ACCESS|Não é possível acessar os registros ou a memória.|  
|E_DIA_VALUE|Erro na computação de um valor (por exemplo, divisão por zero).|  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado durante a depuração para desenrolar a pilha. O objeto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) é implementado pelo aplicativo cliente para receber atualizações para os registros e para fornecer métodos usados pelo `execute` método.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
