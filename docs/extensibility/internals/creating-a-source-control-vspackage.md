---
title: Criando um Pacote VS de Controle de Origem | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709185"
---
# <a name="create-a-source-control-vspackage"></a>Crie um controle de origem VSPackage
Essa documentação inclui links para a visão geral da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]arquitetura de um pacote de controle de origem integrado com , a API que é definida pelas interfaces a serem implementadas e os serviços a serem consumidos, e uma amostra que ilustra uma implementação simples do pacote de controle de origem.

 Com um vsPackage de controle de origem, você pode [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]criar um caminho de integração profunda para que o controle de origem se integre com . Ele permite que o pacote contorne a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ui de controle de origem padrão hospedada [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] por , responda às solicitações de controle de origem do sistema de projeto e interaja com componentes como **o Solution Explorer**. O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] empodera-se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parceiros com um mecanismo para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] criar um VSPackage que possa se integrar com o uso de um modelo de serviço.

## <a name="in-this-section"></a>Nesta seção
- [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Discute o pacote de controle de origem, que é uma alternativa mais avançada [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ao plug-in de controle de origem para implementar recursos de controle de origem em .

- [Arquitetura](../../extensibility/internals/source-control-vspackage-architecture.md)

 Apresenta um diagrama e explica os componentes de um pacote de controle de origem.

- [Recursos](../../extensibility/internals/source-control-vspackage-features.md)

 Descreve as várias características de um pacote de controle de origem.

- [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Descreve a estrutura do VSPackage que um pacote de controle de origem deve implementar para uma integração profunda.

## <a name="related-sections"></a>Seções relacionadas
- [Criar um plug-in de controle de origem](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Discute como criar um plug-in de controle de origem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que forneça a funcionalidade de controle de origem na interface do usuário de controle de origem (UI).

- [Controle de origem](../../extensibility/internals/source-control.md)

 Discute as opções para implementar o controle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de origem como uma característica integrada de .
