---
title: Função GetVstoSolutionMetadata
description: Saiba como a API do GetVstoSolutionMetadata dá suporte à infraestrutura do Office e não se destina a ser usada diretamente do seu código.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eaf58f312afd379fb1f16d208c323777ec725231
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860601"
---
# <a name="getvstosolutionmetadata-function"></a>Função GetVstoSolutionMetadata
  Esta API dá suporte à infraestrutura do Office e não se destina a ser usada diretamente do seu código.

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
 Se a função for realizada com sucesso, ela retornará **S_OK**. Se a função falhar, será exibido um código de erro.
