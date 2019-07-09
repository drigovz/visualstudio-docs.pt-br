---
title: Coletar um rastreamento ETL com PerfView
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: baae89b7bf45a4848c571f75e37c6cc0d203d459
ms.sourcegitcommit: 6f7a740750b2cd17ea2275c3d046caebc9782917
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518182"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Coletar um rastreamento ETL com PerfView

PerfView é uma ferramenta que cria arquivos ETL (log de rastreamento de eventos) com base no [Rastreamento de Eventos para Windows](/windows/desktop/ETW/event-tracing-portal) que pode ser útil na solução de alguns tipos de problemas do Visual Studio. Ocasionalmente, quando você relata algum problema, a equipe de produto pode solicitar que você execute o PerfView para coletar informações adicionais.

## <a name="install-perfview"></a>Instalar o PerfView

Baixe o PerfView no [Centro de Download da Microsoft](http://www.microsoft.com/download/details.aspx?id=28567).

## <a name="run-perfview"></a>Executar o PerfView

1. Clique com o botão direito do mouse em **PerfView.exe** no Windows Explorer e, como administrador, escolha **Executar como administrador**
1. No menu Coletar, escolha **Coletar**
1. Marque **Zip**, **Mesclar** e **Tempo de Thread**.
1. Aumente **MB Circular** para 1000.
1. Altere **Dir atual** para salvar os rastreamentos ETL em uma pasta especificada e altere o Arquivo de Dados, se você pretende coletar mais de uma vez.
1. Para iniciar a gravação de dados, selecione o botão **Iniciar a Coleta**.
1. Para interromper a gravação de dados, selecione o botão **Parar a Coleta**. O arquivo PrefView.etl.zip será salvo no diretório especificado.

O PerfView pode armazenar apenas os dados mais recentes que se encaixam em seu buffer. Portanto, tente interromper a coleta logo depois que o Visual Studio for iniciado para congelá-lo ou diminuí-lo. Não colete por mais de 30 segundos depois de alcançar um problema.

Para obter mais informações, assista ao [Tutorial do PerfView no Channel9](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).