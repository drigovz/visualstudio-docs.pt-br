---
title: Visão geral (debug interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7374b03da42e34e8ac3be8c7cc570769d9cfd1ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179203"
---
# <a name="overview-debug-interface-access-sdk"></a>Visão geral (SDK de Acesso à Interface de Depuração)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use o DIA SDK para acessar as informações de depuração da Microsoft. O DIA SDK fornece um conjunto de API baseado em COM que elimina a necessidade de reescrever seu código sempre que a Microsoft alterar o formato das informações de depuração. O DIA SDK também permite que você leia a partir de um conjunto selecionado de versões anteriores de informações de depuração, localizadas nos arquivos. PDB e. dbg gerados pelas [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] versões 5,0 e posteriores.  
  
 Cada interface na DIA SDK representa um objeto COM diferente, exceto quando declarado de outra forma. Interfaces adicionais e, portanto, objetos adicionais, são criadas por meio de consultas explícitas, como [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) ou [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), em vez de chamar `QueryInterface` ponteiros de interface existentes.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
