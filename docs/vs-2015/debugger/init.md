---
title: Init | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a630906fa2a23a87853e8a835f155cda3ec06ecc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252389"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prepara o componente no aplicativo de diagnóstico de gráficos para capturar e registrar informações de gráficos em um arquivo de log de gráficos ativamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `vsgLogGetter`  
 Uma entidade que pode ser chamada — como uma função, ponteiro de função, lambda ou objeto de função — que usa como parâmetros o comprimento de um buffer composto `wchar_t` e um ponteiro para esse buffer e retorna `void`. Quando invocada, a entidade que pode ser chamada determina o nome do arquivo que será usado para registrar informações de gráficos e grava-o buffer especificado antes de retornar.  
  
## <a name="remarks"></a>Comentários  
 O `Init` função é chamada automaticamente quando uma instância das `VsgDbg` classe for construída, especificando o `bDefaultInit` parâmetro de seu construtor como `true`; caso contrário, `Init` deve ser chamado explicitamente antes de você pode capturar ativamente e registre informações de gráficos.  
  
 Você pode finalizar a fechar os elementos gráficos ativos arquivo de log e chamando `UnInit`e, em seguida, capturar e registrar informações de gráficos mais para um novo arquivo de log de elementos gráficos chamando `Init` novamente. Você pode repetir isso quantas vezes você deseja criar gráficos independentes de vários arquivos de log usando o mesmo `VsgDbg` instância.  
  
## <a name="see-also"></a>Consulte também  
 [UnInit](../debugger/init.md)



