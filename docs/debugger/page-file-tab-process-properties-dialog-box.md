---
title: Guia arquivo de paginação, caixa de diálogo Propriedades do processo | Microsoft Docs
description: Use a guia arquivo de página das propriedades do processo para examinar o arquivo de paginação de um processo. Este artigo descreve as configurações disponíveis.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 47f4a2e9215cb2e98fdfefecdf978cb4a442ad84
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975050"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Guia Arquivo de Paginação, Caixa de diálogo Propriedades do Processo
Use a guia **arquivo de página** para examinar o arquivo de paginação de um processo. Para exibir a [caixa de diálogo Propriedades do processo](../debugger/process-properties-dialog-box.md), mova o foco para uma janela de [exibição de processos](../debugger/processes-view.md) . Selecione qualquer nó de processo na árvore e escolha **Propriedades** no menu **Exibir** .

 As configurações a seguir estão disponíveis na guia **arquivo de paginação** :

|Entrada|Descrição|
|-----------|-----------------|
|**Bytes de Arquivo de Paginação**|O número atual de páginas que esse processo está usando no arquivo de paginação. O arquivo de paginação armazena páginas de dados usadas pelo processo, mas não contidas em outros arquivos. O arquivo de paginação é usado por todos os processos, e a falta de espaço no arquivo de paginação pode causar erros enquanto outros processos estão em execução.|
|**Bytes de Arquivo de Paginação de Pico**|O número máximo de páginas que esse processo usou no arquivo de paginação.|
|**Falhas de página**|O número de falhas de página pelos threads em execução neste processo. Uma falha de página ocorre quando uma thread faz referência a uma página de memória virtual que não está no seu conjunto de trabalho na memória principal. Portanto, a página não será recuperada do disco se estiver na lista de espera e, portanto, já está na memória principal, ou se estiver sendo usada por outro processo com o qual a página é compartilhada.|