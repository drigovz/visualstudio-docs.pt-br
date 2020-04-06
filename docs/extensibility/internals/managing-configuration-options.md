---
title: Gerenciamento de opções de configuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e18c308d74f8c20267c286c47d0e89bf82cd2850
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707303"
---
# <a name="managing-configuration-options"></a>Gerenciando opções de configuração
Ao criar um novo tipo de projeto, você deve gerenciar as configurações de configuração de projeto e solução que determinam como seu projeto será construído, embalado, implantado e executado. Os tópicos a seguir discutem a configuração de projetos e soluções.

## <a name="in-this-section"></a>Nesta seção
- [Visão geral](../../extensibility/internals/configuration-options-overview.md)

 Descreve como os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos podem suportar várias configurações.

- [Páginas de propriedades](../../extensibility/internals/property-pages.md)

 Explica que os usuários podem visualizar e alterar propriedades dependentes da configuração do projeto e propriedades independentes usando páginas de propriedade.

- [Configuração da solução](../../extensibility/internals/solution-configuration.md)

 Fornece informações sobre o que é armazenado nas configurações da solução e como as configurações da solução direcionam o comportamento dos comandos **Iniciar** e **Construir.**

- [Objeto de configuração de projeto](../../extensibility/internals/project-configuration-object.md)

 Explica como o objeto de configuração do projeto gerencia a exibição de informações de configuração para a ia de ia.

- [Configuração de projeto para compilar](../../extensibility/internals/project-configuration-for-building.md)

 Explica como uma lista de configurações de solução para uma determinada solução é gerenciada pela caixa de diálogo Configurações de **solução.**

- [Configuração de projeto para gerenciar a implantação](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Define o ato de implantação [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e as duas formas de apoiar projetos que apoiam a implantação.

- [Configuração de projeto para saída](../../extensibility/internals/project-configuration-for-output.md)

 Explica os processos de compilação que cada configuração pode suportar e as interfaces e métodos pelos quais os itens de saída podem ser disponibilizados.

## <a name="related-sections"></a>Seções relacionadas
- [Tipos de projeto](../../extensibility/internals/project-types.md)

 Fornece uma visão geral dos projetos como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] os blocos básicos de construção do ambiente de desenvolvimento integrado (IDE). Links são fornecidos para tópicos adicionais que explicam como os projetos controlam a construção e compilação de códigos.
