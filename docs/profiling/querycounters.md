---
title: QueryCounters | Microsoft Docs
description: Saiba como a opção QueryCounters lista os contadores de desempenho de CPU (hardware) disponíveis no computador.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d33b6fe42f786218bf78825a356a25edff2b31ae
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720430"
---
# <a name="querycounters"></a>QueryCounters
A opção **QueryCounters** lista os contadores de desempenho de CPU (hardware) que estão disponíveis no computador.

 **QueryCounters** deve ser a única opção na linha de comando.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /QueryCounters
```

#### <a name="parameters"></a>Parâmetros
 Nenhum

## <a name="remarks"></a>Comentários
 Quando você estiver usando o método de instrumentação, o criador de perfil pode coletar os valores de um ou mais contadores de desempenho de CPU em cada evento de coleta de dados. Quando você estiver usando o método de criação de perfil de amostragem, você pode especificar um evento de contador e o número de ocorrências de eventos a ser usado como o intervalo de amostragem.

 Processadores diferentes expõem diferentes contadores de desempenho da CPU. O criador de perfil define um conjunto de contadores genéricos que pode ser usado em quase todos os processadores. A opção **QueryCounters** lista os nomes dos contadores genéricos tanto os nomes dos contadores que são específicos para o processador.

## <a name="see-also"></a>Confira também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
