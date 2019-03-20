---
title: Método IActiveScriptProfilerCallback3::SetWebWorkerId | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0798a23b4c8ad4e5859bec73ebfed47a56b322d6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151291"
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