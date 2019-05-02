---
title: Função SccEndBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0662e4c4d1d71e2c9ae0e8f40ff21868d6b9a5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433260"
---
# <a name="sccendbatch-function"></a>Função SccEndBatch
Essa função conclui um lote de operações de controle do código-fonte. Esses lotes não podem ser aninhados.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parâmetros
 nenhuma.

## <a name="return-value"></a>Valor retornado
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Lote de operações concluídas com êxito.|
|SCC_E_UNKNOWNERROR|Falha não específica.|

## <a name="remarks"></a>Comentários
 Lotes de controle do código-fonte são usados para executar as mesmas operações de controle do código-fonte entre vários projetos ou vários contextos. Lotes podem ser usados para eliminar as caixas de diálogo redundantes a experiência do usuário durante uma operação em lote. O [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e o `SccEndBatch` função são usados como um par para indicar o início e no final de uma operação. Eles não podem ser aninhados.

## <a name="see-also"></a>Consulte também
- [Funções de API de plug-in da controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)