---
title: Visão geral (depuração de acesso à Interface SDK) | Microsoft Docs
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
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 741e4ee8e7b05db9d8b63b296569e268d7144dc7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193603"
---
# <a name="overview-debug-interface-access-sdk"></a>Visão geral (SDK de Acesso à Interface de Depuração)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use o SDK do DIA para acessar as informações de depuração da Microsoft. O DIA SDK fornece uma COM baseado em conjunto de APIs que elimina a necessidade de reescrever o código sempre que a Microsoft altera o formato das informações de depuração. O DIA SDK também permite que você leia de um conjunto selecionado de versões anteriores de informações de depuração, localizado em arquivos. PDB e. dbg gerados por [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] versões 5.0 e posteriores.  
  
 Cada interface no DIA SDK representa um objeto COM diferentes, exceto quando indicado de outra forma. Interfaces adicionais e, portanto, objetos adicionais, são criados por meio de consultas explícitas, como [idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md) ou [idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), em vez de chamar `QueryInterface` em ponteiros de interface existente.  
  
## <a name="see-also"></a>Consulte também  
 [Idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)



