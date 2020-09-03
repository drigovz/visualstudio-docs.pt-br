---
title: Cópia (captura programática) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161509"
---
# <a name="copy-programmatic-capture"></a>Copiar (captura programática)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Copia o conteúdo do arquivo de log de gráficos ativo (. vsglog) em um novo arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szNewVSGLog`  
 O nome de arquivo do novo arquivo de log de gráficos.  
  
## <a name="remarks"></a>Comentários  
 Para copiar as informações de gráficos para um novo arquivo, você já deve ter capturado algumas informações gráficas; caso contrário, nada acontece.
