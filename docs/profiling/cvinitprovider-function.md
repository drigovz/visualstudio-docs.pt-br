---
title: Função CvInitProvider | Microsoft Docs
description: Consulte informações de referência para a função do SDK do Visualizador de simultaneidade CvInitProvider (biblioteca C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d1b41d9d62bbf5a159ec3a9d60f4e2edf5cc115
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686500"
---
# <a name="cvinitprovider-function"></a>Função CvInitProvider
Inicializa o provedor de marcador. Deve ser chamada antes das outras funções do SDK da Visualização Simultânea.

## <a name="syntax"></a>Sintaxe

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parâmetros
 `pGuid` GUID do provedor. Não pode ser NULL.

 `ppProvider` Endereço de uma variável de saída que armazenará o contexto de provedor. Não pode ser NULL.

## <a name="return-value"></a>Valor retornado
 S_OK quando o provedor é inicializado com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkers.h*

## <a name="see-also"></a>Consulte também
- [Referência da biblioteca C++](../profiling/cpp-library-reference.md)