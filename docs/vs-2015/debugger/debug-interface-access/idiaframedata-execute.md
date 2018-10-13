---
title: 'Idiaframedata:: execute | Microsoft Docs'
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
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8949e0a9c0f7aac0a648df9de8ee50c4f32292c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197763"
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
 [in] Uma [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) o objeto que mantém o estado de registradores do quadro.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores retornados para esse método.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Não é possível executar um quadro de pilha no código de prólogo.|  
|E_DIA_SYNTAX|Erro encontrado no programa de quadro de análise.|  
|E_DIA_FRAME_ACCESS|Não é possível a registros de acesso ou memória.|  
|E_DIA_VALUE|Erro no cálculo de um valor (por exemplo, a divisão por zero).|  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado durante a depuração para desenrolar a pilha. O [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objeto é implementado pelo aplicativo cliente para receber atualizações para os registros e fornecer métodos usados pelo `execute` método.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



