---
title: 'Como: Especificar o tempo de execução do .NET Framework | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7fd60568b0e92e26aa9370e6521a9da9d7d5ed27
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968239"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Como: Especificar o tempo de execução do .NET Framework

Com o lançamento do [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], os aplicativos podem ser compostos de módulos que foram compilados usando versões diferentes do tempo de execução do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Por padrão, as Ferramentas de Criação de Perfil do Visual Studio analisam o primeiro tempo de execução que é carregado pelo aplicativo. Você pode especificar o tempo de execução a ser analisado ao iniciar um aplicativo com o criador de perfil e ao anexar o criador de perfil a um aplicativo que já esteja em execução.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Para especificar o tempo de execução do .NET Framework a ser analisado ao iniciar um aplicativo com o criador de perfil

1. No **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho, clique em **Propriedades** e, em seguida, clique em **Avançado**.

     A caixa de listagem **Versão do CLR de Destino** exibe **Automático** e as versões de tempo de execução do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que estão instaladas no computador.

2. Execute uma das seguintes etapas:

    - Clique na versão do CLR que você deseja analisar.

    - Clique em **Automático** para analisar a primeira versão que é carregada pelo aplicativo.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Para especificar o tempo de execução do .NET Framework a ser analisado ao anexar o criador de perfil a um aplicativo

1. No menu **Analisar**, aponte para **Criador de Perfil** e, em seguida, clique em **Anexar/Desanexar**.

2. Na caixa de diálogo **Anexar Criador de Perfil a Processo**, clique no processo cujo perfil deseja criar.

     A caixa de listagem **Versão do CLR de Destino** exibe **Automático** e as versões de tempo de execução do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que estão instaladas no computador.

3. Execute uma das seguintes etapas:

    - Clique na versão do CLR que você deseja analisar.

    - Clique em **Automático** para analisar a versão que é carregada quando o criador de perfil se anexa ao aplicativo.