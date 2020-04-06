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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700236"
---
# <a name="sccuninitialize-function"></a>Função SccUninitialize
Esta função limpa quaisquer alocações ou conexões abertas criadas por uma chamada anterior para o [SccInitialize](../extensibility/sccinitialize-function.md) em preparação para desligar o plug-in de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>parâmetros
 pvContext

[em] O ponteiro para a estrutura de contexto plug-in de controle de origem criada no [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A limpeza foi concluída com sucesso.|

## <a name="remarks"></a>Comentários
 O plug-in de controle de origem é responsável pela preparação para ser desligado e pela liberação da memória que o plug-in alocou para a estrutura do contexto. A função é chamada uma vez para cada instância de um plug-in. Uma chamada para o [SccInitialize](../extensibility/sccinitialize-function.md) precede esta chamada. Nenhum projeto ainda pode ser aberto no `SccUninitialize`momento da chamada para .

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
