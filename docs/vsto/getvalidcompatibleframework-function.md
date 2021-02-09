---
title: Função GetValidCompatibleFramework
description: Saiba como a API do GetValidCompatibleFramework dá suporte à infraestrutura do Office e não se destina a ser usada diretamente do seu código.
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
ms.openlocfilehash: b089f954c59219461c8e267ee6e88e47015fc794
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860614"
---
# <a name="getvalidcompatibleframework-function"></a>Função GetValidCompatibleFramework
  Esta API dá suporte à infraestrutura do Office e não se destina a ser usada diretamente do seu código.

## <a name="syntax"></a>Sintaxe

```csharp
HRESULT WINAPI GetValidCompatibleFramework(
    LPCWSTR lpwszCompatibleFrameworksXML,
    BSTR* pbstrValidFrameworkTag
);
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|Não use.|
|*pbstrValidFrameworkTag*|Não use.|

## <a name="return-value"></a>Valor retornado
 Se a função for realizada com sucesso, ela retornará **S_OK**. Se a função falhar, será exibido um código de erro.
