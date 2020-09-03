---
title: 'Erro: o SQL pode&#39;t localizar SSDEBUGPS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25462a99bd3e773f03af3918a9e25d11ed006c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185206"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erro: o SQL pode&#39;t localizar SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll é o componente do host de depuração do SQL Server.  
  
 Esse erro ocorre quando você está tentando iniciar a depuração e indica que o arquivo especificado não está presente no computador do [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. As causas possíveis são que a instalação da Depuração Remota nunca foi executada ou que de alguma forma esse arquivo foi excluído.  
  
 Há duas maneiras de resolver este erro: executando novamente a instalação da Depuração Remota e copiando o arquivo no computador do [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)].  
  
 Para executar novamente a instalação de depuração remota, siga as instruções em [depuração remota](../debugger/remote-debugging.md).  
  
 Se você puder localizar uma cópia de ssdebugps.dll, poderá copiá-lo no computador do [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. Se houver, o arquivo estará no diretório \Arquivos de Programas\ Common Files\Microsoft Shared\SQL Debugging. Você pode encontrá-lo em outro [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] computador ou em um computador que tenha o [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] instalado.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Para copiar o SSDEBUGPS.dll no computador do SQL Server 2005  
  
1. Copie o arquivo para o diretório com o mesmo nome e o caminho no computador do [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)].  
  
2. Registre-o abrindo o **Prompt de Comando** e executando o seguinte comando:  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```
