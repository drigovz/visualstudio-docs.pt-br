---
title: Função CvIsEnabled | Microsoft Docs
description: Consulte informações de referência para a função do SDK do Visualizador de simultaneidade CvIsEnabled (biblioteca C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0be750f62e248b3d9f837c5baa561765e14bfba5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940937"
---
# <a name="cvisenabled-function"></a>Função CvIsEnabled
Determina se uma sessão habilitou o provedor ETW especificado.

## <a name="syntax"></a>Sintaxe

```C
HRESULT CvIsEnabled(
   _In_ PCV_PROVIDER pProvider
);
HRESULT CvIsEnabledEx(
   _In_ PCV_PROVIDER pProvider,
   _In_ CV_IMPORTANCE level,
   _In_ int category
);
```

#### <a name="parameters"></a>Parâmetros
 `category` Categoria.

 `level` Nível de prioridade.

 `pProvider` Objeto de provedor válido. Não pode ser NULL.

## <a name="return-value"></a>Valor retornado
 S_OK se o provedor estiver habilitado no momento. S_FALSE se o provedor estiver desabilitado no momento. Código de erro em caso de erros. Use a macro FAILED para verificar a condição de erro e depois verifique se S_OK/S_FALSE.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkers.h*

## <a name="see-also"></a>Confira também
- [Referência da biblioteca C++](../profiling/cpp-library-reference.md)