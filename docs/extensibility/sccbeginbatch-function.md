---
title: Função SccBeginBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c7982d8c8c0d71f8c79e9b808be5453d384882d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701193"
---
# <a name="sccbeginbatch-function"></a>Função SccBeginBatch
Esta função inicia uma seqüência em lote de operações de controle de origem. O [SccEndBatch](../extensibility/sccendbatch-function.md) será chamado para terminar o lote. Estes lotes podem não estar aninhados.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccBeginBatch(void);
```

### <a name="parameters"></a>parâmetros
 Nenhum.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O lote de operações começou com sucesso.|
|SCC_E_UNKNOWNERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 Os lotes de controle de origem são usados para executar as mesmas operações em vários projetos ou vários contextos. Os lotes podem ser usados para eliminar caixas de diálogo redundantes por projeto da experiência do usuário durante uma operação em lote. A `SccBeginBatch` função e o [SccEndBatch](../extensibility/sccendbatch-function.md) são usados como um par de funções para indicar o início e o fim de uma operação. Eles não podem ser aninhados. `SccBeginBatch`define uma bandeira indicando que uma operação em lote está em andamento.

 Enquanto uma operação em lote estiver em vigor, o plug-in de controle de origem deve apresentar no máximo uma caixa de diálogo para qualquer pergunta ao usuário e aplicar a resposta dessa caixa de diálogo em todas as operações subseqüentes.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccEndBatch](../extensibility/sccendbatch-function.md)
