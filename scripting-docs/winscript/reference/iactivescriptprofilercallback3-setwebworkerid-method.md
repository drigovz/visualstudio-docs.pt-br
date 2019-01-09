---
title: Método IActiveScriptProfilerCallback3::SetWebWorkerId | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4025dbee7b8b5b246163a1919aec335a8863937
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094427"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>Método IActiveScriptProfilerCallback3::SetWebWorkerId
Notifica o criador de perfil sobre a ID do trabalho a ser usado para esta sessão de criação de perfil. Se a função não estiver em execução no contexto da página, esse método não é invocado. O valor de `webWorkerId` aumenta em incrementos de 1 para cada funcionário, começando em 1. Os valores de ID não pretendem ser estável, além de uma sessão e correspondem somente à ordem em que os trabalhos foram criados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `webWorkerId`  
 A ID do trabalho web.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor de retorno desse método é ignorado pelo mecanismo de script.