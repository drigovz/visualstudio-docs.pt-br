---
title: 'Erro: SQL pode&#39;t consegue localizar SSDEBUGPS | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 854105ea5d94f6d3b09ce73a23ec45ccab9e797c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850492"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erro: SQL pode&#39;t consegue localizar SSDEBUGPS

SSDEBUGPS.dll é o componente do host de depuração do SQL Server.

Esse erro ocorre quando você está tentando iniciar a depuração e indica que o arquivo especificado não está presente no computador do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. As causas possíveis são que a instalação da Depuração Remota nunca foi executada ou que de alguma forma esse arquivo foi excluído.

Há duas maneiras de resolver este erro: executando novamente a instalação da Depuração Remota e copiando o arquivo no computador do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

Para executar novamente a instalação da depuração remota, siga as instruções em [depuração remota](../debugger/remote-debugging.md).

Se você puder localizar uma cópia de ssdebugps.dll, poderá copiá-lo no computador do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. Se houver, o arquivo estará no diretório \Arquivos de Programas\ Common Files\Microsoft Shared\SQL Debugging. Você pode encontrá-lo em outro [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] computador, ou em um computador que tenha o Visual Studio 2005 instalado.

Para copiar o SSDEBUGPS.dll no computador do SQL Server 2005:

1. Copie o arquivo para o diretório com o mesmo nome e o caminho no computador do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)].

2. Registre-o abrindo o **Prompt de Comando** e executando o seguinte comando:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
