---
title: Guia espaço, caixa de diálogo Propriedades do processo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 563d54c39b4d9ce3bb2d76a9e531161c2c4ee5b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62929817"
---
# <a name="space-tab-process-properties-dialog-box"></a>Guia Espaço, Caixa de diálogo Propriedades do Processo
Use a guia **espaço** para examinar o espaço de endereço de um processo. Para exibir a [caixa de diálogo Propriedades do processo](../debugger/process-properties-dialog-box.md), mova o foco para uma janela de [exibição de processos](../debugger/processes-view.md) . Selecione qualquer nó de processo na árvore e escolha **Propriedades** no menu **Exibir** .

 As configurações a seguir estão disponíveis na guia **espaço** :

|Entrada|Descrição|
|-----------|-----------------|
|**Exibir para espaço marcado como**|Use essa caixa de listagem para selecionar a categoria de espaço (imagem, mapeada, reservada ou não atribuída).|
|**Bytes Executáveis**|Para a categoria selecionada, a soma de todo o espaço de endereço que esse processo está usando. A memória executável é a memória que pode ser executada por programas, mas pode não ser lida ou gravada.|
|**Bytes de Execução-Somente Leitura**|Para a categoria selecionada, a soma de todo o espaço de endereço em uso com propriedades somente leitura que esse processo está usando. A memória do exec-somente leitura é a memória que pode ser executada, bem como a leitura.|
|**Bytes de Execução-Leitura-Gravação**|Para a categoria selecionada, a soma de todo o espaço de endereço em uso com as propriedades de leitura/gravação que esse processo está usando. O exec-Read-write memory é a memória que pode ser executada por programas, bem como leitura e modificação.|
|**Bytes de cópia de gravação de exec**|Para a categoria selecionada, a soma de todo o espaço de endereço que pode ser executado por programas, bem como leitura e gravação. Esse tipo de proteção é usado quando a memória precisa ser compartilhada entre processos. Se os processos de compartilhamento só lêem a memória, eles usarão a mesma memória. Se um processo de compartilhamento desejar acesso de gravação, uma cópia dessa memória será feita para o processo.|
|**Bytes Não Acessíveis**|Para a categoria selecionada, a soma de todo o espaço de endereço que impede um processo de usá-lo. Uma violação de acesso é gerada se a tentativa de gravação ou leitura for tentada.|
|**Bytes Somente Leitura**|Para a categoria selecionada, a soma de todo o espaço de endereço que pode ser executado, bem como a leitura.|
|**Bytes de Leitura-Gravação**|Para a categoria selecionada, a soma de todo o espaço de endereço que permite leitura e gravação.|
|**Bytes de Gravação-Cópia**|Para a categoria selecionada, a soma de todo o espaço de endereço que permite o compartilhamento de memória para leitura, mas não para gravação. Quando os processos estão lendo essa memória, eles podem compartilhar a mesma memória. No entanto, quando um processo de compartilhamento deseja ter acesso de leitura/gravação a essa memória compartilhada, uma cópia dessa memória é feita para gravação.|