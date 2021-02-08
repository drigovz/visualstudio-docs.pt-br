---
title: Guia memória, caixa de diálogo Propriedades do processo | Microsoft Docs
description: Use a guia memória das propriedades do processo para exibir como um processo usa a memória. Há informações sobre espaço usado, espaço compartilhado e espaço virtual usado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a1bf0409dacdd6cb2f7de65462f637124a5cecd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845016"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Guia Memória, Caixa de diálogo Propriedades do Processo
Use a guia **memória** para mostrar como um processo usa a memória. Para exibir a [caixa de diálogo Propriedades do processo](../debugger/process-properties-dialog-box.md), mova o foco para uma janela de [exibição de processos](../debugger/processes-view.md) . Selecione qualquer nó de processo na árvore e escolha **Propriedades** no menu **Exibir** .

 As configurações a seguir estão disponíveis na guia **memória** :

|Entrada|Descrição|
|-----------|-----------------|
|**Bytes Virtuais**|O tamanho atual (em bytes) do espaço de endereço virtual que o processo está usando. O uso do espaço de endereço virtual não implica necessariamente o uso correspondente do disco ou das páginas de memória principal. No entanto, o espaço virtual é finito e o uso excessivo pode limitar a capacidade do processo de carregar bibliotecas.|
|**Bytes virtuais de pico**|O número máximo de bytes de espaço de endereço virtual que o processo usou em qualquer momento.|
|**Conjunto de Trabalho**|O conjunto de páginas de memória tocadas recentemente pelos threads no processo. Se a memória livre no computador estiver acima de um limite, as páginas serão mantidas no Conjunto de Trabalho de um processo mesmo que não estejam em uso. Quando a memória livre cai abaixo de um limite, as páginas são cortadas do conjunto de trabalho. Se forem necessários, eles serão reproduzidos por falha de software no conjunto de trabalho antes de deixarem a memória principal.|
|**Conjunto de trabalho de pico**|O número máximo de páginas no conjunto de trabalho desse processo em qualquer ponto no tempo.|
|**Bytes de pool paginável**|A quantidade atual de pool paginável que o processo alocou. O pool paginável é uma área de memória do sistema em que os componentes do sistema operacional adquirem espaço à medida que realizam suas tarefas deformadas. Páginas de pool paginável podem ser paginadas para o arquivo de paginação quando não acessadas pelo sistema por períodos de tempo prolongados.|
|**Bytes de pool não paginável**|O número atual de bytes no pool não paginável alocado pelo processo. O pool não paginável é uma área de memória do sistema em que o espaço é adquirido pelos componentes do sistema operacional à medida que realizam suas tarefas deformadas. Páginas de pool não paginável não podem ser paginadas para o arquivo de paginação; Eles permanecem na memória principal, desde que sejam alocados.|
|**Bytes Particulares**|O número atual de bytes que esse processo alocou e que não pode ser compartilhado com outros processos.|
|**Bytes livres**|O espaço de endereço virtual não utilizado total desse processo.|
|**Bytes reservados**|A quantidade total de memória virtual reservada para uso futuro por esse processo.|
|**Bytes de imagens livres**|A quantidade de espaço de endereço virtual que não está em uso ou reservada por imagens dentro desse processo.|
|**Bytes de imagens reservadas**|A soma de toda a memória virtual reservada por imagens é executada dentro desse processo.|