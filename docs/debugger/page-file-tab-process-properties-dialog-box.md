---
title: Guia arquivo de paginação, caixa de diálogo de propriedades do processo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25dc3b0aca1b58c18ae4038540c14fc4dbfe4036
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904101"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Guia Arquivo de Paginação, Caixa de diálogo Propriedades do Processo
Use o **arquivo de paginação** guia para examinar o arquivo de paginação de um processo. Para exibir o [caixa de diálogo de propriedades do processo](../debugger/process-properties-dialog-box.md), mova o foco para um [exibição de processos](../debugger/processes-view.md) janela. Selecione qualquer nó de processo na árvore e escolha **propriedades** da **exibição** menu.

 As configurações a seguir estão disponíveis na **arquivo de paginação** guia:

|Entrada|Descrição|
|-----------|-----------------|
|**Bytes de Arquivo de Paginação**|O número atual de páginas que esse processo está usando no arquivo de paginação. O arquivo de paginação armazena as páginas de dados usado pelo processo, mas não está contido em outros arquivos. O arquivo de paginação é usado por todos os processos e falta de espaço no arquivo de paginação pode causar erros durante a execução de outros processos.|
|**Bytes de Arquivo de Paginação de Pico**|O número máximo de páginas que esse processo tem usado no arquivo de paginação.|
|**Falhas de página**|O número de falhas de página por segmentos em execução nesse processo. Uma falha de página ocorre quando um thread faz referência a uma página de memória virtual que não está no conjunto de trabalho na memória principal. Portanto, a página não será recuperada do disco se ele estiver na lista de espera e, portanto, já na memória principal, ou se ele está sendo usado por outro processo com a página é compartilhada.|