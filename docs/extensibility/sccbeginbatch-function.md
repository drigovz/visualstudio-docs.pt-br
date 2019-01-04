---
title: Função SccBeginBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2e0ae1dd4d01018d9637e5722d8079222afbf3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869119"
---
# <a name="sccbeginbatch-function"></a>Função SccBeginBatch
Essa função inicia uma sequência de lote de operações de controle do código-fonte. O [SccEndBatch](../extensibility/sccendbatch-function.md) será chamado para finalizar o lote. Esses lotes não podem ser aninhados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor retornado  
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Lote de operações começou com êxito.|  
|SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Lotes de controle do código-fonte são usados para executar as mesmas operações em vários projetos ou vários contextos. Lotes podem ser usados para eliminar as caixas de diálogo do projeto de redundantes a experiência do usuário durante uma operação em lote. O `SccBeginBatch` função e o [SccEndBatch](../extensibility/sccendbatch-function.md) são usados como um par de função para indicar o início e no final de uma operação. Eles não podem ser aninhados. `SccBeginBatch` define um sinalizador que indica que uma operação em lote está em andamento.  
  
 Enquanto uma operação em lote estiver em vigor, o plug-in de controle do código-fonte deve apresentar no máximo uma caixa de diálogo para qualquer pergunta ao usuário e aplicar a resposta nessa caixa de diálogo em todas as operações subsequentes.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in da controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)