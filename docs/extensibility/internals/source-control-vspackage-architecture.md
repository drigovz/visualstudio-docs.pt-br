---
title: Arquitetura de VSPackage de controle do código-fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9484aabd0080b0a44d75a8a5f6d90d9217d74b8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723347"
---
# <a name="source-control-vspackage-architecture"></a>Arquitetura do VSPackage de controle do código-fonte
Um pacote de controle de origem é um VSPackage que usa serviços fornecidos pelo IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Em retorno, um pacote de controle de origem fornece sua funcionalidade como um serviço de controle do código-fonte. Além disso, um pacote de controle de origem é uma alternativa mais versátil do que um plug-in de controle do código-fonte para integrar o controle do código-fonte em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Um plug-in de controle do código-fonte que implementa a API de plug-in de controle do código-fonte obedece a um contrato estrito. Por exemplo, um plug-in não pode substituir a interface do usuário do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] padrão. Além disso, a API de plug-in de controle do código-fonte não permite que um plug-in implemente seu próprio modelo de controle do código-fonte. Um pacote de controle de origem, no entanto, supera essas duas limitações. Um pacote de controle de origem tem controle total sobre a experiência de controle do código-fonte de um usuário [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Além disso, um pacote de controle de origem pode usar seu próprio modelo de controle do código-fonte e lógica e pode definir todas as interfaces do usuário relacionadas ao controle do código-fonte.

## <a name="source-control-package-components"></a>Componentes do pacote de controle de origem
 Conforme mostrado no diagrama de arquitetura, um componente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chamado stub de controle do código-fonte é um VSPackage que integra um pacote de controle de origem com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 O stub de controle do código-fonte lida com as tarefas a seguir.

- Fornece a interface do usuário comum que é necessária para o registro do pacote de controle de origem.

- Carrega um pacote de controle de origem.

- Define um pacote de controle de origem como ativo/inativo.

  O stub de controle do código-fonte procura o serviço ativo para o pacote de controle de origem e roteia todas as chamadas de serviço de entrada do IDE para esse pacote.

  O pacote do adaptador de controle do código-fonte é um pacote de controle de origem especial que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornece. Este pacote é o componente central para dar suporte aos plug-ins de controle do código-fonte com base na API de plug-in de controle do código-fonte. Quando um plug-in de controle do código-fonte é o plug-in ativo, o stub de controle do código-fonte envia seus eventos para o pacote do adaptador de controle do código-fonte. Por sua vez, o pacote do adaptador de controle do código-fonte se comunica com o plug-in de controle do código-fonte usando a API de plug-in de controle do código-fonte e também fornece uma interface do usuário padrão que é comum para todos os plug-ins de controle do

  Quando um pacote de controle de origem é o pacote ativo, por outro lado, o stub de controle do código-fonte se comunica diretamente com o pacote usando as interfaces do pacote de controle de origem [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. O pacote de controle de origem é responsável por hospedar sua própria interface do usuário de controle do código-fonte.

  ![Gráfico de arquitetura de controle do código-fonte](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Para um pacote de controle de origem, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] não fornece código de controle do código-fonte ou uma API para integração. Compare isso com a abordagem descrita na criação de [um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md) em que o plug-in de controle do código-fonte tem de implementar um conjunto rígido de funções e retornos de chamada.

  Como qualquer VSPackage, um pacote de controle de origem é um objeto COM que pode ser criado usando `CoCreateInstance`. O VSPackage torna-se disponível para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Quando uma instância é criada, um VSPackage recebe um ponteiro de site e uma interface <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> que fornece o acesso VSPackage aos serviços e interfaces disponíveis no IDE.

  Escrever um pacote de controle de origem baseado em VSPackage requer uma experiência de programação mais avançada do que escrever um plug-in baseado em API de plug-in de controle do código-fonte.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)