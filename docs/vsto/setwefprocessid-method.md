---
title: Método SetWefProcessId
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
ms.openlocfilehash: 1352ccc9318061be4a2f9ad2da7d63715acd6721
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603074"
---
# <a name="setwefprocessid-method"></a>Método SetWefProcessId
  Fornece o identificador do processo que executará o conteúdo de estrutura de extensões da Web (WEF).

## <a name="syntax"></a>Sintaxe

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*dwProcessId*|O identificador de processo que será usado para executar o conteúdo do WEF.|

## <a name="return-value"></a>Valor retornado
 Um valor HRESULT que indica se o método concluída com êxito.

## <a name="remarks"></a>Comentários
 Esse método deve ser chamado depois que o processo de conteúdo do WEF é criado, mas antes de qualquer conteúdo WEF é executado.

 Se você quiser anexar um depurador ao processo de conteúdo do WEF o ambiente de desenvolvimento, o ambiente deve realizar essa operação em sua implementação deste método.
