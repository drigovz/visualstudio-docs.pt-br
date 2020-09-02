---
title: Guia geral, caixa de diálogo Propriedades do processo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6116beb67baf072d9c9762a1e8c67408cc915f29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62849821"
---
# <a name="general-tab-process-properties-dialog-box"></a>Guia Geral, Caixa de diálogo Propriedades do Processo
Use a guia **geral** para saber mais sobre um processo específico. Para exibir a [caixa de diálogo Propriedades do processo](../debugger/process-properties-dialog-box.md), mova o foco para uma janela de [exibição de processos](../debugger/processes-view.md) . Selecione qualquer nó de processo na árvore e escolha **Propriedades** no menu **Exibir** .

 As configurações a seguir estão disponíveis na guia **geral** :

|Entrada|Descrição|
|-----------|-----------------|
|**Nome do módulo**|O nome do módulo.|
|**ID do Processo**|A ID exclusiva desse processo. Os números de ID de processo são reutilizados, portanto, eles identificam um processo somente durante o tempo de vida desse processo. O tipo de objeto de processo é criado quando um programa é executado. Todos os threads em um processo compartilham o mesmo espaço de endereço e têm acesso aos mesmos dados.|
|**Base de Prioridade**|A prioridade base atual deste processo. Os threads em um processo podem aumentar e diminuir sua própria prioridade básica em relação à prioridade base do processo.|
|**Threads**|O número de threads atualmente ativo neste processo.|
|**Tempo de CPU**|Tempo total de CPU gasto nesse processo e seus threads. Igual ao tempo de usuário mais privilegiado.|
|**Tempo do Usuário**|O tempo acumulado que os threads do processo passaram executando código no modo de usuário em threads não ociosos. Os aplicativos são executados no modo de usuário, assim como os subsistemas, como o Gerenciador de janelas e o mecanismo de gráficos.|
|**Tempo Privilegiado**|O tempo total decorrido em que esse processo esteve em execução no modo privilegiado em threads não ociosos. A camada de serviço, as rotinas executivas e o kernel são executados no modo privilegiado. Drivers de dispositivo para a maioria dos dispositivos que não sejam adaptadores gráficos e impressoras também são executados no modo privilegiado. Alguns trabalhos que o Windows faz para seu aplicativo podem aparecer em outros processos de subsistema, além do tempo privilegiado.|
|**Tempo decorrido**|O tempo total decorrido em que esse processo esteve em execução.|