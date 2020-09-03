---
title: Arquitetura de VSPackage de controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3cca9e39714f87024b01ab2c925189aacbe22785
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183401"
---
# <a name="source-control-vspackage-architecture"></a>Arquitetura do VSPackage de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um pacote de controle de origem é um VSPackage que usa os serviços que o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE fornece. Em retorno, um pacote de controle de origem fornece sua funcionalidade como um serviço de controle do código-fonte. Além disso, um pacote de controle de origem é uma alternativa mais versátil do que um plug-in de controle do código-fonte para integrar o controle do código-fonte no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Um plug-in de controle do código-fonte que implementa a API de plug-in de controle do código-fonte obedece a um contrato estrito. Por exemplo, um plug-in não pode substituir a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interface do usuário padrão. Além disso, a API de plug-in de controle do código-fonte não permite que um plug-in implemente seu próprio modelo de controle do código-fonte. Um pacote de controle de origem, no entanto, supera essas duas limitações. Um pacote de controle de origem tem controle total sobre a experiência de controle do código-fonte de um [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usuário. Além disso, um pacote de controle de origem pode usar seu próprio modelo de controle do código-fonte e lógica e pode definir todas as interfaces do usuário relacionadas ao controle do código-fonte.  
  
## <a name="source-control-package-components"></a>Componentes do pacote de controle de origem  
 Conforme mostrado no diagrama de arquitetura, um [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componente chamado stub de controle do código-fonte é um VSPackage que integra um pacote de controle de origem com o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 O stub de controle do código-fonte lida com as tarefas a seguir.  
  
- Fornece a interface do usuário comum que é necessária para o registro do pacote de controle de origem.  
  
- Carrega um pacote de controle de origem.  
  
- Define um pacote de controle de origem como ativo/inativo.  
  
  O stub de controle do código-fonte procura o serviço ativo para o pacote de controle de origem e roteia todas as chamadas de serviço de entrada do IDE para esse pacote.  
  
  O pacote do adaptador de controle do código-fonte é um pacote de controle de origem especial que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornece. Este pacote é o componente central para dar suporte aos plug-ins de controle do código-fonte com base na API de plug-in de controle do código-fonte. Quando um plug-in de controle do código-fonte é o plug-in ativo, o stub de controle do código-fonte envia seus eventos para o pacote do adaptador de controle do código-fonte. Por sua vez, o pacote do adaptador de controle do código-fonte se comunica com o plug-in de controle do código-fonte usando a API de plug-in de controle do código-fonte e também fornece uma interface do usuário padrão que é comum para todos os plug-ins de controle do  
  
  Quando um pacote de controle de origem é o pacote ativo, por outro lado, o stub de controle do código-fonte se comunica diretamente com o pacote usando as [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] interfaces do pacote de controle de origem. O pacote de controle de origem é responsável por hospedar sua própria interface do usuário de controle do código-fonte.  
  
  ![Gráfico de arquitetura de controle do código-fonte](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
  Para um pacote de controle de origem, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o não fornece o código de controle do código-fonte ou uma API para integração. Compare isso com a abordagem descrita na criação de [um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md) em que o plug-in de controle do código-fonte tem de implementar um conjunto rígido de funções e retornos de chamada.  
  
  Como qualquer VSPackage, um pacote de controle de origem é um objeto COM que pode ser criado usando o `CoCreateInstance` . O VSPackage torna-se disponível para o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Quando uma instância é criada, um VSPackage recebe um ponteiro de site e uma <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface que fornece o acesso VSPackage aos serviços e interfaces disponíveis no IDE.  
  
  Escrever um pacote de controle de origem baseado em VSPackage requer uma experiência de programação mais avançada do que escrever um plug-in baseado em API de plug-in de controle do código-fonte.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
