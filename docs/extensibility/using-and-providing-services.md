---
title: Usar e fornecer serviços | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c9b0dbf2122b5a76d557cdd70da27660b886041
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337035"
---
# <a name="using-and-providing-services"></a>Usando e fornecendo serviços
Um serviço é um contrato entre dois VSPackages. Um VSPackage oferece um conjunto específico de interfaces para outro VSPackage consumir. Por exemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oferece o <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de serviço a qualquer VSPackage ele carrega. Esse serviço fornece o <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, que pode ser usado para gravar no log de atividade. Para obter mais informações, confira [Como: Usar o Log de atividades](../extensibility/how-to-use-the-activity-log.md).

 VSPackages podem oferecer serviços de suas próprias por usar o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface...

 O Visual Studio oferece serviços importantes, como o seguinte:

|Serviço IDE|Descrição|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornece acesso ao IDE services lidar com a funcionalidade básica, os VSPackages e o registro.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornece janelas básicas e funcionalidade relacionada à interface do usuário no IDE, como a capacidade de criar ferramentas e janelas de documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornece a funcionalidade básica de relacionadas à solução, como a capacidade de enumerar os projetos, criar novos projetos e monitorar as alterações do projeto.|

## <a name="in-this-section"></a>Nesta seção
- [Fundamentos do serviço](../extensibility/internals/service-essentials.md) apresenta os elementos importantes de um serviço do Visual Studio.

- [Como: Obtenha um serviço](../extensibility/how-to-get-a-service.md) descreve como solicitar (consumir) um serviço.

- [Como: Fornecer um serviço](../extensibility/how-to-provide-a-service.md) discute como fornecer um serviço.

- [Como: Fornecer um serviço assíncrono do Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) discute como fornecer um serviço assíncrono.

- [Como: Solucionar problemas de serviços](../extensibility/how-to-troubleshoot-services.md) aborda problemas comuns e apresenta soluções para eles.

## <a name="related-sections"></a>Seções relacionadas
- [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)