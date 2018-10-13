---
title: 'Idiasession:: Findinjectedsource | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa844e54e925421b11acd5b7280a86711ae1d6ff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227715"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera uma lista de fontes que foi colocada no armazenamento de símbolos por provedores de atributos ou outros componentes do processo de compilação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 srcFile  
 [in] Nome do arquivo de origem pela qual pesquisar.  
  
 ppResult  
 [out] Retorna um [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) objeto que contém uma lista de todas as fontes injetadas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



