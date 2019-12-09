---
title: Função SccBeginBatch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 264d9057bf4f17281d6d8a16ed3a6794004e0e21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189554"
---
# <a name="sccbeginbatch-function"></a>Função SccBeginBatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função inicia uma sequência de lote de operações de controle do código-fonte. O [SccEndBatch](../extensibility/sccendbatch-function.md) será chamado para finalizar o lote. Esses lotes não podem ser aninhados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Lote de operações começou com êxito.|  
|SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Lotes de controle do código-fonte são usados para executar as mesmas operações em vários projetos ou vários contextos. Lotes podem ser usados para eliminar as caixas de diálogo do projeto de redundantes a experiência do usuário durante uma operação em lote. O `SccBeginBatch` função e o [SccEndBatch](../extensibility/sccendbatch-function.md) são usados como um par de função para indicar o início e no final de uma operação. Eles não podem ser aninhados. `SccBeginBatch` define um sinalizador que indica que uma operação em lote está em andamento.  
  
 Enquanto uma operação em lote estiver em vigor, o plug-in de controle do código-fonte deve apresentar no máximo uma caixa de diálogo para qualquer pergunta ao usuário e aplicar a resposta nessa caixa de diálogo em todas as operações subsequentes.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
