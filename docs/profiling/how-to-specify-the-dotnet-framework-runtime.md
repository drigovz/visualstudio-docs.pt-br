---
title: Especificar o runtime do .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 27846b448f7e0667004bd25d24bd447fe43f8e51
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851119"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Como especificar o runtime do .NET Framework

Com o lançamento do .NET Framework 4, os aplicativos podem ser compostos por módulos que foram criados usando diferentes versões do tempo de execução do .NET Framework. Por padrão, as Ferramentas de Criação de Perfil do Visual Studio analisam o primeiro runtime que é carregado pelo aplicativo. Você pode especificar o tempo de execução a ser analisado ao iniciar um aplicativo com o criador de perfil e ao anexar o criador de perfil a um aplicativo que já esteja em execução.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Para especificar o tempo de execução do .NET Framework a ser analisado ao iniciar um aplicativo com o criador de perfil

1. No **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho, clique em **Propriedades** e, em seguida, clique em **Avançado**.

     A caixa de listagem **Versão do CLR de Destino** exibe **Automático** e as versões do runtime do .NET Framework que estão instaladas no computador.

2. Execute uma das seguintes etapas:

    - Clique na versão do CLR que você deseja analisar.

    - Clique em **Automático** para analisar a primeira versão que é carregada pelo aplicativo.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Para especificar o tempo de execução do .NET Framework a ser analisado ao anexar o criador de perfil a um aplicativo

1. No menu **Analisar**, aponte para **Criador de Perfil** e, em seguida, clique em **Anexar/Desanexar**.

2. Na caixa de diálogo **Anexar Criador de Perfil a Processo**, clique no processo cujo perfil deseja criar.

     A caixa de listagem **Versão do CLR de Destino** exibe **Automático** e as versões do runtime do .NET Framework que estão instaladas no computador.

3. Execute uma das seguintes etapas:

    - Clique na versão do CLR que você deseja analisar.

    - Clique em **Automático** para analisar a versão que é carregada quando o criador de perfil se anexa ao aplicativo.
