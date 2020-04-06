---
title: Glossário de depurador de depurador visual studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 954532311fe6b63fc288877a6d41722e6ea47581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713353"
---
# <a name="visual-studio-debugger-glossary"></a>Glossário do depurador do Visual Studio
A seguir estão os [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] termos usados no SDK de depuração.

## <a name="terms"></a>Termos
 ponto de ruptura vinculado Uma abstração para um ponto de ruptura definido em código. Há uma relação um-para-um entre um ponto de ruptura vinculado e uma instrução de ponto de ruptura no fluxo de código. Quando o código é descarregado, os pontos de interrupção vinculados podem desvincular-se.

 Causalidade Fornece a capacidade de rastrear um segmento lógico de execução através de vários segmentos físicos, processos e máquinas, e reconstruir a pilha de chamadas desse segmento lógico em qualquer ponto da vida desse segmento.

 contexto de código Fornece uma abstração de uma posição em código conhecido pelo mecanismo de depuração. Para a maioria das arquiteturas de tempo de execução, um contexto de código é um endereço no fluxo de instruções de um programa. Para línguas não tradicionais, nas quais o código não pode ser representado por instruções, um contexto de código pode ser representado por outros meios.

 caminho de código Representa um ponto de execução no código onde um ramo é tomado ou uma chamada de função é feita. Um rastreamento de pilha é essencialmente uma lista de caminhos de código de chamada de função.

 debug engine (DE) Um componente que permite a depuração de uma arquitetura em tempo de execução. Um mecanismo de depuração funciona em conjunto com o intérprete ou sistema operacional e fornece serviços de depuração, como controle de execução, pontos de interrupção e avaliação de expressão.

 contexto do documento Fornece uma abstração de uma posição em um documento de arquivo de origem conhecido pelo mecanismo de depuração. Para a maioria dos idiomas, um contexto de documento é uma posição em um arquivo de origem. Para idiomas não tradicionais, para os quais o arquivo de origem pode não ser texto, um contexto de documento pode ser representado por alguns outros meios. Veja também *a posição do documento*.

 posição do documento Fornece uma abstração de uma posição em um arquivo de origem conhecido pelo IDE. Para a maioria dos idiomas, uma posição de documento é uma posição em um arquivo de origem. Para línguas não tradicionais, uma posição de documento pode ser representada de outras formas. Veja também *o contexto do documento*.

 ponto de quebra de erro Uma abstração para descrever um erro em um ponto de ruptura pendente. Um ponto de ruptura de erro pode descrever um erro na localização do ponto de ruptura pendente, a expressão associada ao ponto de ruptura pendente ou outras informações que impedem que o ponto de ruptura pendente seja vinculado a um local de código.

 contexto de avaliação Fornece uma abstração de um contexto de programação para avaliação de expressão. Normalmente, um contexto de avaliação é um escopo. Ao fazer a avaliação da expressão em um contexto de expressão, o contexto de expressão fornece regras de escopo que correspondem ao seu ponto de criação. Por exemplo, um contexto de expressão criado em um quadro de pilha fornecerá o contexto para avaliar variáveis locais, parâmetros de método, membros de classe (se aplicável) e variáveis globais.

 exceção interceptada Uma exceção que é interceptada por um motor de depuração, mesmo que nenhum mecanismo de manuseio de exceção esteja em vigor no quadro de pilha atual.

 JustMyCode O conceito de depurar apenas o código que pertence a um usuário e ignorar todos os códigos intermediários, como o código do sistema — mesmo que o código-fonte esteja disponível para esse código do sistema.

 ponto de interrupção pendente Fornece uma abstração para pontos de interrupção antes, durante e depois que o código é carregado e uma maneira de virtualizar pontos de interrupção. Um ponto de ruptura pendente:

- Contém todas as informações necessárias para vincular um ponto de ruptura ao código em um ou mais programas.

- Pode se ligar a vários locais de código em um ou mais programas.

- Nunca se liga ao código.

  Cada código de tempo é carregado, todos os pontos de interrupção pendentes em um programa são verificados para ver se eles podem vincular. Diz-se que um ponto de interrupção pendente contém todos os pontos de interrupção vinculados que ele vincula.

  processo Um processo físico Win32. Um processo pode conter vários programas. Veja também *o programa*.

  programa Um único namespace em execução dentro de uma arquitetura de tempo de execução particular. Veja também *o processo*.

  o SDM (Session Debug Manager, gerenciador de depuração) gerencia qualquer número de mecanismos de depuração de qualquer número de programas em vários processos em qualquer número de máquinas. No nível básico, o SDM é um multiplexador de motores de depuração. Além disso, o SDM fornece uma visão unificada da sessão de depuração para o IDE.

  quadro de pilha Representa o estado de computação em um quadro específico e nível particular de chamadas de função aninhadas.

  thread A noção generalizada de execução de instruções baseada em pilha satisfazendo em pelo menos um programa.

  ponto de ruptura de aviso Uma abstração para descrever um aviso em um ponto de ruptura pendente. Um ponto de ruptura de aviso descreve uma razão pela qual o ponto de ruptura pendente ainda não está vinculado a um local de código. Isso pode ser que o código ainda não tenha sido carregado para o local descrito pelo ponto de ruptura pendente, ou por algum outro motivo.

## <a name="see-also"></a>Confira também
- [Extensibilidade do depurador do Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
