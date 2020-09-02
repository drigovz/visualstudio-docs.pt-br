---
title: Guia arquivo de paginação, caixa de diálogo Propriedades do processo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24fdba37be2373623d94f03e45dc5e8a41a74b84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192724"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Guia Arquivo de Paginação, Caixa de diálogo Propriedades do Processo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use a guia **arquivo de página** para examinar o arquivo de paginação de um processo. Para exibir a [caixa de diálogo Propriedades do processo](../debugger/process-properties-dialog-box.md), mova o foco para uma janela de [exibição de processos](../debugger/processes-view.md) . Selecione qualquer nó de processo na árvore e escolha **Propriedades** no menu **Exibir** .  
  
 As configurações a seguir estão disponíveis na guia **arquivo de paginação** :  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Bytes de Arquivo de Paginação**|O número atual de páginas que esse processo está usando no arquivo de paginação. O arquivo de paginação armazena páginas de dados usadas pelo processo, mas não contidas em outros arquivos. O arquivo de paginação é usado por todos os processos, e a falta de espaço no arquivo de paginação pode causar erros enquanto outros processos estão em execução.|  
|**Bytes de Arquivo de Paginação de Pico**|O número máximo de páginas que esse processo usou no arquivo de paginação.|  
|**Falhas de página**|O número de falhas de página pelos threads em execução neste processo. Uma falha de página ocorre quando uma thread faz referência a uma página de memória virtual que não está no seu conjunto de trabalho na memória principal. Portanto, a página não será recuperada do disco se estiver na lista de espera e, portanto, já está na memória principal, ou se estiver sendo usada por outro processo com o qual a página é compartilhada.|
