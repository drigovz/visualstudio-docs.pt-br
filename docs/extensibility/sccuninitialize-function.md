---
title: Função SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e7de3572b17bf47859a64451149a269988c91e5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836677"
---
# <a name="sccuninitialize-function"></a>Função SccUninitialize
Essa função limpa todas as alocações ou conexões abertas criadas por uma chamada anterior para o [SccInitialize](../extensibility/sccinitialize-function.md) em preparação para desligar o plug-in de controle do código-fonte.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parâmetros
 pvContext

no O ponteiro para a estrutura de contexto de plug-in de controle do código-fonte criada no [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A limpeza foi concluída com êxito.|

## <a name="remarks"></a>Comentários
 O plug-in de controle do código-fonte é responsável por se preparar para desligar e liberar memória que o plug-in alocou para a estrutura de contexto. A função é chamada uma vez para cada instância específica de um plug-in. Uma chamada para o [SccInitialize](../extensibility/sccinitialize-function.md) precede essa chamada. Nenhum projeto ainda pode estar aberto no momento da chamada para `SccUninitialize` .

## <a name="see-also"></a>Consulte também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
