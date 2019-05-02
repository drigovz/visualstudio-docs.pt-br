---
title: Copiar (Captura programática) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa79ffc2081ba92b905838658fe6aa758a675192
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923675"
---
# <a name="copy-programmatic-capture"></a>Copiar (captura programática)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Copia o conteúdo do arquivo de log (. vsglog) de elementos gráficos ativos em um novo arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szNewVSGLog`  
 O nome do arquivo do novo arquivo de log de gráficos.  
  
## <a name="remarks"></a>Comentários  
 Para copiar as informações de gráficos para um novo arquivo, você deve já capturou algumas informações de gráficos; Caso contrário, nada acontece.
