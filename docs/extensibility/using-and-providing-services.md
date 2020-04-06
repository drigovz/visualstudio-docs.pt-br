---
title: Utilização e Prestação de Serviços | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698735"
---
# <a name="using-and-providing-services"></a>Usando e fornecendo serviços
Um serviço é um contrato entre dois VSPackages. Um VSPackage oferece um conjunto específico de interfaces para outro VSPackage consumir. Por exemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> oferece o serviço a qualquer VSPackage que ele carrega. Este serviço <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> fornece a interface, que pode ser usada para escrever no registro de atividades. Para obter mais informações, [consulte Como: Usar o Registro de Atividades](../extensibility/how-to-use-the-activity-log.md).

 VsPackages podem oferecer serviços próprios usando a <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface..

 O Visual Studio oferece serviços importantes, como o seguinte:

|Serviço IDE|Descrição|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fornece acesso aos serviços iDE que lidam com funcionalidade básica, VSPackages e registro.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornece janelas básicas e funcionalidades relacionadas à UI no IDE, como a capacidade de criar ferramentas e janelas de documentos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornece funcionalidades básicas relacionadas à solução, como a capacidade de enumerar projetos, criar novos projetos e monitorar mudanças de projetos.|

## <a name="in-this-section"></a>Nesta seção
- [Essenciais de serviço](../extensibility/internals/service-essentials.md) Apresenta os elementos importantes de um serviço visual studio.

- [Como: Obter um serviço](../extensibility/how-to-get-a-service.md) Discute como solicitar (consumir) um serviço.

- [Como: Fornecer um Serviço](../extensibility/how-to-provide-a-service.md) Discute como prestar um serviço.

- [Como: Fornecer um serviço de estúdio visual assíncrono](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Discute como fornecer um serviço assíncrono.

- [Como: Serviços de solução de problemas](../extensibility/how-to-troubleshoot-services.md) Discute problemas comuns e apresenta soluções para eles.

## <a name="related-sections"></a>Seções relacionadas
- [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)
