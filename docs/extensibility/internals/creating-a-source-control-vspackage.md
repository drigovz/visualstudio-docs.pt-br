---
title: Criando um controle do código-fonte VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709185"
---
# <a name="create-a-source-control-vspackage"></a>Criar um controle do código-fonte VSPackage
Esta documentação inclui links para a visão geral da arquitetura de um pacote de controle de origem integrado ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , a API que é definida pelas interfaces a serem implementadas e os serviços a serem consumidos e um exemplo que ilustra uma implementação simples do pacote de controle do código-fonte.

 Com um VSPackage de controle do código-fonte, você pode criar um caminho de integração profundo para o controle do código-fonte a ser integrado ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Ele permite que o pacote ignore a interface do usuário do controle do código-fonte padrão hospedada pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , responda às solicitações de controle do código-fonte do sistema de projeto e interaja com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes como **Gerenciador de soluções**. O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] capacita os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parceiros com um mecanismo para criar um VSPackage que pode ser integrado ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando um modelo de serviço.

## <a name="in-this-section"></a>Nesta seção
- [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Discute o pacote de controle do código-fonte, que é uma alternativa mais avançada para o plug-in de controle do código-fonte para implementar recursos de controle do código-fonte no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Arquitetura](../../extensibility/internals/source-control-vspackage-architecture.md)

 Apresenta um diagrama e explica os componentes de um pacote de controle do código-fonte.

- [Recursos](../../extensibility/internals/source-control-vspackage-features.md)

 Descreve os vários recursos de um pacote de controle do código-fonte.

- [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Descreve a estrutura do VSPackage que um pacote de controle do código-fonte deve implementar para integração profunda.

## <a name="related-sections"></a>Seções relacionadas
- [Criar um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Discute como criar um plug-in de controle do código-fonte que fornece funcionalidade de controle do código-fonte na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário do controle do código-fonte (IU).

- [Controle do código-fonte](../../extensibility/internals/source-control.md)

 Discute as opções para implementar o controle do código-fonte como um recurso integrado do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
