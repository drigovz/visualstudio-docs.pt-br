---
title: Como filtrar relatórios da linha de comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bd6462f9159a2926c6dfa45dcadff860cce9ca1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778928"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Como filtrar relatórios por meio da linha de comando
Ao usar as opções para o comando **VSPerfReport**, você pode filtrar relatórios para um segmento de tempo específico do arquivo de dados de criação de perfil ou restringir os dados a um ou mais processos ou threads. Para obter mais informações sobre esse comando, consulte [VSPerfReport](../profiling/vsperfreport.md).

|Opções|Descrição|
|-------------|-----------------|
|**StartTime:**[*Valor*]|Mostrar apenas os dados coletados depois do valor (em milissegundos).|
|**Tempo final:**[*Valor*]|Mostrar apenas os dados coletados antes do valor (em milissegundos).|
|**FilterFile:** `VSPFFile`|Especifica a localização de um arquivo de filtro gerado a partir da janela **Visual Studio Performance Report.**|
|**MsFilter:**[*StartTime,Duração*]|Mostrar apenas os dados de `StartTime` até a duração de `Duration` (em milissegundos).|
|**Processo:**[*Pid*]|Mostrar somente os dados do processo especificado.|
|**Linha:**[*ThreadID*]|Mostra apenas os dados do thread especificado.|
|**Tópico:**[*ThreadID,ProcessID*]|Mostrar somente os dados do thread especificado associados ao processo especificado.|
