---
title: Glossário do depurador do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 19d82f006bb1c37981f60e1a0b2710588eb0053c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204774"
---
# <a name="visual-studio-debugger-glossary"></a>Glossário do depurador do Visual Studio
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Veja a seguir os termos usados no [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] SDK de depuração.  
  
## <a name="terms"></a>Termos  
 ponto de interrupção associado  
 Uma abstração para um ponto de interrupção definido no código. Há uma relação um-para-um entre um ponto de interrupção associado e uma instrução de ponto de interrupção no fluxo de código. Quando o código é descarregado, os pontos de interrupção associados podem desassociar.  
  
 causalidade  
 Fornece a capacidade de acompanhar um thread lógico de execução em vários threads, processos e máquinas físicos e reconstruir a pilha de chamadas desse thread lógico em qualquer ponto no tempo de vida desse thread.  
  
 contexto de código  
 Fornece uma abstração de uma posição no código conhecida pelo mecanismo de depuração. Para a maioria das arquiteturas de tempo de execução, um contexto de código é um endereço no fluxo de instruções de um programa. Para linguagens não tradicionais, em que o código não pode ser representado por instruções, um contexto de código pode ser representado por outros meios.  
  
 caminho do código  
 Representa um ponto de execução no código em que uma ramificação é obtida ou uma chamada de função é feita. Um rastreamento de pilha é essencialmente uma lista de caminhos de código de chamada de função.  
  
 mecanismo DE depuração (DE)  
 Um componente que permite a depuração de uma arquitetura de tempo de execução. Um mecanismo de depuração funciona em conjunto com o interpretador ou o sistema operacional e fornece serviços de depuração, como controle de execução, pontos de interrupção e avaliação de expressão.  
  
 contexto de documento  
 Fornece uma abstração de uma posição em um documento de arquivo de origem conhecido pelo mecanismo de depuração. Para a maioria dos idiomas, um contexto de documento é uma posição em um arquivo de origem. Para idiomas não tradicionais, para os quais o arquivo de origem pode não ser texto, um contexto de documento pode ser representado por outros meios. Consulte também *posição do documento*.  
  
 posição do documento  
 Fornece uma abstração de uma posição em um arquivo de origem conhecido pelo IDE. Para a maioria dos idiomas, uma posição de documento é uma posição em um arquivo de origem. Para idiomas não tradicionais, uma posição de documento pode ser representada de outras maneiras. Consulte também *contexto de documento*.  
  
 ponto de interrupção de erro  
 Uma abstração para descrever um erro em um ponto de interrupção pendente. Um ponto de interrupção de erro pode descrever um erro no local do ponto de interrupção pendente, a expressão associada ao ponto de interrupção pendente ou outras informações que impedem que o ponto de interrupção pendente seja vinculado a um local de código.  
  
 contexto de avaliação  
 Fornece uma abstração de um contexto de programação para avaliação de expressão. Normalmente, um contexto de avaliação é um escopo. Ao fazer a avaliação de expressão em um contexto de expressão, o contexto de expressão fornece regras de escopo que correspondem a seu ponto de criação. Por exemplo, um contexto de expressão criado em um quadro de pilha fornecerá o contexto para avaliar variáveis locais, parâmetros de método, membros de classe (se aplicável) e variáveis globais.  
  
 exceção interceptada  
 Uma exceção que é interceptada por um mecanismo de depuração, mesmo que nenhum mecanismo de manipulação de exceção esteja em vigor no registro de ativação atual.  
  
 JustMyCode  
 O conceito de depuração somente do código que pertence a um usuário e ignora todo o código intermediário, como código do sistema, mesmo se o código-fonte estiver disponível para esse código do sistema.  
  
 ponto de interrupção pendente  
 Fornece uma abstração para pontos de interrupção antes, durante e após o código ser carregado e uma maneira de virtualizar pontos de interrupção. Um ponto de interrupção pendente:  
  
- Contém todas as informações necessárias para associar um ponto de interrupção ao código em um ou mais programas.  
  
- Pode associar a vários locais de código em um ou mais programas.  
  
- Nunca se associa a código.  
  
  Cada vez que o código é carregado, todos os pontos de interrupção pendentes em um programa são verificados para ver se eles podem se associar. Um ponto de interrupção pendente é dito para conter todos os pontos de interrupção associados que ele associa.  
  
  process  
  Um processo do Win32 físico. Um processo pode conter vários programas. Consulte também *programa*.  
  
  programa  
  Um único namespace em execução dentro de uma arquitetura de tempo de execução específica. Consulte também *processar*.  
  
  Gerenciador de depuração de sessão (SDM)  
  Gerencia qualquer número de mecanismos de depuração Depurando qualquer número de programas em vários processos em qualquer número de computadores. No nível básico, o SDM é um multiplexador de mecanismos de depuração. Além disso, o SDM fornece uma exibição unificada da sessão de depuração para o IDE.  
  
  registro de ativação  
  Representa o estado de computação em um determinado quadro e um nível específico de chamadas de função aninhadas.  
  
  thread  
  A noção generalizada da execução de instrução baseada em pilha executada em pelo menos um programa.  
  
  ponto de interrupção de aviso  
  Uma abstração para descrever um aviso em um ponto de interrupção pendente. Um ponto de interrupção de aviso descreve um motivo pelo qual o ponto de interrupção pendente ainda não está associado a um local de código. Isso pode ser que o código ainda não foi carregado para o local descrito pelo ponto de interrupção pendente ou por algum outro motivo.  
  
## <a name="see-also"></a>Consulte Também  
 [Extensibilidade do depurador do Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
