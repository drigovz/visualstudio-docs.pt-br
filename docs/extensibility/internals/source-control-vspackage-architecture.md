---
title: Arquitetura VSPackage de Controle de Fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705081"
---
# <a name="source-control-vspackage-architecture"></a>Arquitetura do VSPackage de controle do código-fonte
Um pacote de controle de origem é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um VSPackage que usa serviços que o IDE fornece. Em troca, um pacote de controle de origem fornece sua funcionalidade como um serviço de controle de origem. Além disso, um pacote de controle de origem é uma alternativa mais versátil do que um plug-in de controle de origem para integrar o controle de origem em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Um plug-in de controle de origem que implementa a API plug-in de controle de origem cumpre um contrato rigoroso. Por exemplo, um plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não pode substituir a interface de usuário padrão (UI). Além disso, a API plug-in de controle de fonte não permite que um plug-in implemente seu próprio modelo de controle de origem. Um pacote de controle de origem, no entanto, supera ambas essas limitações. Um pacote de controle de origem tem controle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] completo sobre a experiência de controle de origem de um usuário. Além disso, um pacote de controle de origem pode usar seu próprio modelo de controle de origem e lógica, e pode definir todas as interfaces de usuário relacionadas ao controle de origem.

## <a name="source-control-package-components"></a>Componentes do pacote de controle de origem
 Como mostrado no diagrama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de arquitetura, um componente chamado Source Control Stub é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]um VSPackage que integra um pacote de controle de origem com .

 O Stub de Controle de Origem lida com as seguintes tarefas.

- Fornece a ui comum necessária para o registro do pacote de controle de origem.

- Carrega um pacote de controle de origem.

- Define um pacote de controle de origem como ativo/inativo.

  O Source Control Stub procura o serviço ativo para o pacote de controle de origem e encaminha todas as chamadas de serviço recebidas do IDE para esse pacote.

  O Pacote adaptador de controle de origem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é um pacote especial de controle de origem que fornece. Este pacote é o componente central para suporte a plug-ins de controle de origem com base na API plug-in de controle de origem. Quando um plug-in de controle de origem é o plug-in ativo, o Stub de controle de origem envia seus eventos para o Pacote adaptador de controle de origem. Por sua vez, o Pacote adaptador de controle de origem comunica-se com o plug-in de controle de origem usando a API plug-in de controle de origem e também fornece uma IU padrão que é comum para todos os plug-ins de controle de origem.

  Quando um pacote de controle de origem é o pacote ativo, por outro lado, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] o Stub de controle de origem se comunica diretamente com o pacote usando as interfaces do Pacote de Controle de Origem. O pacote de controle de origem é responsável por hospedar sua própria ui de controle de origem.

  ![Gráfico de arquitetura de controle do código-fonte](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Para um pacote de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controle de origem, não fornece código de controle de origem ou uma API para integração. Contraste isso com a abordagem descrita no [Creating a Source Control Plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md) onde o plug-in de controle de origem tem que implementar um conjunto rígido de funções e retornos de chamadas.

  Como qualquer VSPackage, um pacote de controle de origem é `CoCreateInstance`um objeto COM que pode ser criado usando . O VSPackage se disponibiliza ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Quando uma instância é criada, um VSPackage recebe <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> um ponteiro de site e uma interface que fornece o acesso do VSPackage aos serviços e interfaces disponíveis no IDE.

  Escrever um pacote de controle de origem baseado em VSPackage requer uma experiência de programação mais avançada do que escrever um plug-in baseado em API baseado em Controle de Fonte.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
