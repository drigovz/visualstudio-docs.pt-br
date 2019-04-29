---
title: Função GetValidCompatibleFramework
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
ms.openlocfilehash: b975a4b4b2c1b4ae3f6ef0f1d6d23769bb4c77c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788690"
---
# <a name="getvalidcompatibleframework-function"></a>Função GetValidCompatibleFramework
  Essa API dá suporte à infraestrutura do Office e não se destina a ser usado diretamente do seu código.

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
 Se a função obtiver êxito, retorna **S_OK**. Se a função falhar, ele retornará um código de erro.
