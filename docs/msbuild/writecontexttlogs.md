---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c06c77ef75f279be85435fc507cc82ef6984f66
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828388"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Grava arquivos de log para o contexto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 [in] `intermediateDirectory`  
 O diretório no qual deseja armazenar o log de acompanhamento.  
  
 [in] `tlogRootName`  
 O nome raiz do nome do arquivo de log.  
  
## <a name="return-value"></a>Valor retornado  
 Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o contexto de acompanhamento foi criado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** *FileTracker.h*  
  
## <a name="see-also"></a>Consulte também  
 [WriteAllTLogs](../msbuild/writealltlogs.md)