---
title: Depurando aplicativos ASP.NET implantados | Microsoft Docs
description: Use o Visual Studio para depurar um aplicativo ASP.NET implantado anexando-se ao processo de trabalho e garantindo que o depurador tenha acesso a símbolos para o aplicativo.
ms.custom: SEO-VS-2020
ms.date: 06/30/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 9b298d756754743635fe3de10c8b72d3195ff3f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872801"
---
# <a name="debugging-deployed-aspnet-applications"></a>Depurando aplicativos ASP.NET implantados
Para usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para depurar um aplicativo implantado, você deverá anexar ao processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e verificar se o depurador tem acesso aos símbolos para o aplicativo. Você também deve localizar e abrir os arquivos de origem para o aplicativo. Para obter mais informações, consulte [especificar o símbolo (. pdb) e os arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [como localizar o nome do processo ASP.net](../debugger/how-to-find-the-name-of-the-aspnet-process.md)e [os requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Se você anexar ao [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo de trabalho para depuração e atingir um ponto de interrupção, todo o código gerenciado no processo de trabalho será interrompido. Interromper todo o código gerenciado no processo de trabalho pode causar uma parada de trabalho para todos os usuários no servidor. Antes de depurar em um servidor de produção, considere o impacto potencial no trabalho de produção.

O processo para anexar ao processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] é o mesmo que anexar a qualquer outro processo remoto. Quando você está anexado, se não tiver o projeto correto aberto, uma caixa de diálogo aparecerá quando o aplicativo for interrompido. Essa caixa de diálogo solicita o local dos arquivos de origem para o aplicativo. O nome do arquivo que você especifica na caixa de diálogo deve corresponder ao nome de arquivo especificado nos símbolos de depuração no servidor Web. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Para configurar a depuração remota no IIS, consulte [depuração remota ASP.net em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Muitos aplicativos Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] fazem referência às DLLs que contêm a lógica de negócios ou outro código útil. Essa referência copia a DLL do computador local para a pasta \bin do diretório virtual do aplicativo Web quando você implanta seu aplicativo. Quando você estiver depurando, lembre-se de que o aplicativo Web está referenciando essa cópia da DLL e não a cópia em seu computador local.

## <a name="see-also"></a>Confira também
- [Depurar aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Instruções: habilitar a depuração para aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Como localizar o nome do processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Especificar os arquivos de origem e símbolo (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)