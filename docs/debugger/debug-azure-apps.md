---
title: Depurar serviços do Azure | Microsoft Docs
description: Você pode depurar os serviços do Azure com o Visual Studio. Use os links neste artigo para saber mais sobre as várias maneiras de fazer isso.
ms.custom: SEO-VS-2020
ms.date: 09/14/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
ms.assetid: 3d434de3-ee5f-419d-9a94-ac4ac02d635b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- azure
ms.openlocfilehash: a77f1291621e84eb2e13075a791e9c6735447137
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857616"
---
# <a name="debug-azure-services-in-visual-studio"></a>Depurar serviços do Azure no Visual Studio

Você pode usar o Visual Studio para depurar os serviços do Azure em diferentes cenários:

Para depurar um aplicativo de produção hospedado em:

- Azure App serviço, usando Visual Studio Enterprise, consulte [debug live ASP.net apps using the depurador de instantâneos](../debugger/debug-live-azure-applications.md).

- Azure App serviço ou Service Fabric, usando Application Insights, consulte [depurar instantâneos em exceções em aplicativos .net](/azure/application-insights/app-insights-snapshot-debugger).

- Máquina virtual do Azure ou conjunto de dimensionamento de máquinas virtuais do Azure, consulte [depurar máquinas virtuais do azure ASP.net e conjuntos de dimensionamento de máquina virtual do Azure ao vivo usando o depurador de instantâneos](../debugger/debug-live-azure-virtual-machines.md).

- Serviço kubernetes do Azure, consulte [depurar live ASP.net serviços do Azure kubernetes usando o depurador de instantâneos](../debugger/debug-live-azure-kubernetes.md).

Para depuração remota:

- ASP.NET no IIS (serviço de Azure App ou uma VM do Azure), consulte [depuração remota ASP.net no Azure](remote-debugging-azure.md).

- ASP.NET no Azure Service Fabric, consulte [depurar um aplicativo de Service Fabric remoto](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)

## <a name="see-also"></a>Consulte também

- [Depurando no Visual Studio](../debugger/index.yml)
