---
title: Método SetWefProcessId
description: Saiba como o método SetWefProcessId fornece o identificador de processo que executará o conteúdo do WEF (Web Extensions Framework).
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
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882402"
---
# <a name="setwefprocessid-method"></a>Método SetWefProcessId
  Fornece o identificador do processo que executará o conteúdo do WEF (Web Extensions Framework).

## <a name="syntax"></a>Sintaxe

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*dwProcessId*|O identificador do processo que será usado para executar o conteúdo do WEF.|

## <a name="return-value"></a>Valor retornado
 Um valor HRESULT que indica se o método foi concluído com êxito.

## <a name="remarks"></a>Comentários
 Esse método deve ser chamado depois que o processo de conteúdo WEF é criado, mas antes de qualquer conteúdo de WEF ser executado.

 Se você quiser que o ambiente de desenvolvimento anexe um depurador ao processo de conteúdo do WEF, o ambiente deverá executar essa operação em sua implementação desse método.
