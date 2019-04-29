---
title: Função GetVstoSolutionMetadata
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7714e78e897e6c8b391a6c30e9a548671ce80c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796035"
---
# <a name="getvstosolutionmetadata-function"></a>Função GetVstoSolutionMetadata
  Essa API dá suporte à infraestrutura do Office e não se destina a ser usado diretamente do seu código.

## <a name="syntax"></a>Sintaxe

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|Não use.|
|*ppSolutionInfo*|Não use.|

## <a name="return-value"></a>Valor retornado
 Se a função obtiver êxito, retorna **S_OK**. Se a função falhar, ele retornará um código de erro.
