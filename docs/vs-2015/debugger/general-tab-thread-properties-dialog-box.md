---
title: Guia geral, caixa de diálogo Propriedades do thread | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b1a8e6fd583f6035fc84f0c86adcee059562235d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159951"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Guia Geral, Caixa de diálogo Propriedades do Thread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use essa caixa de diálogo para saber mais sobre um thread específico. Para exibir essa caixa de diálogo, mova o foco para uma janela de [exibição de threads](../debugger/threads-view.md) ou abra a [exibição mensagens](../debugger/messages-view.md) e expanda uma mensagem. Selecione qualquer nó de thread na árvore e, em seguida, escolha **Propriedades** no menu **Exibir** .  
  
 A caixa de diálogo **Propriedades do thread** contém um painel, a guia **geral** . As seguintes configurações estão disponíveis:  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Nome do módulo**|O nome do módulo.|  
|**ID do thread**|A ID exclusiva deste thread. Observe que os números de ID de thread são reutilizados; eles identificam um thread somente pelo tempo de vida desse thread.|  
|**ID do Processo**|A ID exclusiva desse processo. Os números de ID de processo são reutilizados, portanto, eles identificam um processo somente durante o tempo de vida desse processo. O tipo de objeto de processo é criado quando um programa é executado. Todos os threads em um processo compartilham o mesmo espaço de endereço e têm acesso aos mesmos dados. Escolha esse valor para exibir as propriedades da ID do processo.|  
|**Estado da Thread**|O estado atual do thread. Um thread em execução está usando um processador; um thread em espera está prestes a usar um. Um thread pronto está aguardando para usar um processador porque ele não é gratuito. Um thread em transição está aguardando a execução de um recurso, por exemplo, aguardando que sua pilha de execução seja paginada no disco. Um thread em espera não precisa do processador porque está aguardando a conclusão de uma operação periférica ou um recurso para se tornar livre.|  
|**Motivo de Espera**|Isso é aplicável somente quando o thread está no estado de espera. Os pares de eventos são usados para se comunicar com subsistemas protegidos.|  
|**Tempo de CPU**|Tempo total de CPU gasto nesse processo e seus threads. Igual a tempo de usuário + tempo privilegiado.|  
|**Tempo do Usuário**|O tempo total decorrido que esse thread gastou na execução do código no modo de usuário. Os aplicativos são executados no modo de usuário, assim como os subsistemas, como o Gerenciador de janelas e o mecanismo de gráficos.|  
|**Tempo Privilegiado**|O tempo total decorrido que esse thread gastou na execução do código no modo privilegiado. Quando um serviço de sistema do Windows é chamado, o serviço geralmente é executado no modo privilegiado para obter acesso a dados privados do sistema. Esses dados são protegidos do acesso por threads em execução no modo de usuário. As chamadas para o sistema podem ser explícitas, ou podem ser implícitas, como quando ocorre uma falha de página ou uma interrupção.|  
|**Tempo decorrido**|O tempo total decorrido (em segundos) durante o qual esse thread esteve em execução.|  
|**Prioridade Atual**|A prioridade dinâmica atual deste thread. Os threads em um processo podem aumentar e diminuir sua própria prioridade básica em relação à prioridade base do processo.|  
|**Prioridade de Base**|A prioridade base atual deste thread.|  
|**Endereço inicial**|Iniciando o endereço virtual para este thread.|  
|**PC do Usuário**|O contador de programa do usuário para o thread.|  
|**Opções de Contexto**|O número de opções de um thread para outro. As opções de thread podem ocorrer dentro de um único processo ou entre processos. Uma opção de thread pode ser causada por um thread que solicite informações a outro, ou por um thread que está sendo admitido quando um thread de prioridade mais alta se torna pronto para ser executado.|
