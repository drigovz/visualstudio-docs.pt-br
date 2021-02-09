---
title: Configurar destinos e tarefas | Microsoft Docs
description: Configure destinos e tarefas do MSBuild para execução fora do processo com o MSBuild para que você possa direcionar contextos diferentes daquele em que você está executando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5548478e5404c69acc92d7ca7dc4deb6a2e29fdf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922548"
---
# <a name="configure-targets-and-tasks"></a>Configurar destinos e tarefas

Você pode configurar destinos do MSBuild e tarefas para execução fora de processo com o MSBuild para que você possa direcionar contextos diferentes daqueles que você está executando. Por exemplo, você pode direcionar um aplicativo do .NET Framework 2.0 de 32 bits, enquanto o computador de desenvolvimento está em execução em um sistema de operacional de 64 bits do .NET Framework 4.5. Você também pode direcionar os computadores que executam o .NET Framework 4 ou anterior. A combinação de 32 ou 64 bits e a versão específica do .NET Framework é conhecida como o *contexto de destino*.

## <a name="installation"></a>Instalação

  Caso deseje instalar o MSBuild separadamente do Visual Studio, baixe o pacote de instalação em [Download do MSBuild](https://www.microsoft.com/download/details.aspx?id=40760). Instale também as versões do .NET Framework que deseja usar.

## <a name="targets-and-tasks"></a>Destinos e tarefas

 O MSBuild executa certas tarefas de build fora do processo para destinar para um conjunto maior de contextos.  Por exemplo, um MSBuild de 32 bits pode executar uma tarefa de build em um processo de 64 bits para destinar um computador de 64 bits. Isso é controlado pelos argumentos `UsingTask` e parâmetros `Task`. Os destinos instalados pelo .NET Framework 4.5 definem esses parâmetros e argumentos e nenhuma alteração é necessária para compilar aplicativos para os vários contextos de destino.

 Se quiser criar seu próprio contexto de destino, você deverá definir esses parâmetros e argumentos adequadamente. Examine o arquivo *Microsoft.Common.targets* do .NET Framework 4.5 e o arquivo *Microsoft.Common.Tasks* para obter exemplos.  Para obter informações sobre como criar uma tarefa personalizada que pode trabalhar com vários contextos de destino ou como modificar as tarefas existentes, confira [Como configurar destinos e tarefas](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Confira também

- [Multiplataforma](../msbuild/msbuild-multitargeting-overview.md)
