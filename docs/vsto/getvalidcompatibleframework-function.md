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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 96f536b3ab8e28b87a59a637fcf6dbaadeb21bf7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845070"
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
