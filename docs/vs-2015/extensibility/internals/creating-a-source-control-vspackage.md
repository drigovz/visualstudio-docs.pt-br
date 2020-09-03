---
title: Criando um controle do código-fonte VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1516cf358a4488ff02e650f6c703a1761a94a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196960"
---
# <a name="creating-a-source-control-vspackage"></a>Criar um VSPackage de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta documentação inclui links para a visão geral da arquitetura de um pacote de controle de origem integrado ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , a API que é definida pelas interfaces a serem implementadas e os serviços a serem consumidos e um exemplo que ilustra uma implementação simples do pacote de controle do código-fonte.  
  
 Com um VSPackage de controle do código-fonte, você pode criar um caminho de integração profundo para o controle do código-fonte a ser integrado ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ele permite que o pacote ignore a interface do usuário do controle do código-fonte padrão hospedada pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , responda às solicitações de controle do código-fonte do sistema de projeto e interaja com [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componentes como **Gerenciador de soluções**. O [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] capacita os [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] parceiros com um mecanismo para criar um VSPackage que pode ser integrado ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usando um modelo de serviço.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Discute o pacote de controle do código-fonte, que é uma alternativa mais avançada para o plug-in de controle do código-fonte para implementar recursos de controle do código-fonte no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Arquitetura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Apresenta um diagrama e explica os componentes de um pacote de controle do código-fonte.  
  
 [Recursos](../../extensibility/internals/source-control-vspackage-features.md)  
 Descreve os vários recursos de um pacote de controle do código-fonte.  
  
 [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Descreve a estrutura do VSPackage que um pacote de controle do código-fonte deve implementar para integração profunda.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criando um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Discute como criar um plug-in de controle do código-fonte que fornece funcionalidade de controle do código-fonte na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interface do usuário do controle do código-fonte (IU).  
  
 [Controle do código-fonte](../../extensibility/internals/source-control.md)  
 Discute as opções para implementar o controle do código-fonte como um recurso integrado do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
