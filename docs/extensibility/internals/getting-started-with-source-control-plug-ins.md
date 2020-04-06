---
title: Começando com plug-ins de controle de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efc21e07830614d9d3041b2d2d231fd82c652114
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708342"
---
# <a name="get-started-with-source-control-plug-ins"></a>Comece com plug-ins de controle de origem
Para criar um plug-in de controle de origem, você deve criar uma DLL que implemente as funções [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] definidas na API plug-in de controle de fonte e, em seguida, registrar a DLL para torná-la disponível para uso no controle da versão de código-fonte.

 Três versões da API plug-in de controle de origem (versões 1.1, 1.2 e 1.3) estão disponíveis para plug-ins de controle de origem. A API plug-in de controle de origem documentada aqui é a versão 1.3. Ele foi projetado para ser totalmente compatível com plug-ins de controle de origem suportando as versões 1.1 e 1.2. As novidades da versão [1.3 do Plug-in de controle de fonte](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) detalham os novos recursos suportados na versão mais recente da API plug-in de controle de fonte.

## <a name="in-this-section"></a>Nesta seção
- [Como: Instalar um plug-in de controle de origem](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Descreve como fazer as entradas de registro que são necessárias para conectar um DLL de controle de origem.

- [O que há de novo na API plug-in de controle de fonte versão 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Fornece uma breve visão geral das alterações feitas na API plug-in de controle de fonte na versão 1.3.

- [O que há de novo na API plug-in de controle de fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Fornece uma breve visão geral das alterações feitas na API plug-in de controle de fonte na versão 1.2.

## <a name="related-sections"></a>Seções relacionadas
- [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md)

 Fornece uma lista completa de todos os elementos da API plug-in de controle de fonte.

- [Criar um plug-in de controle de origem](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Define o SDK plug-in de controle de origem e descreve os recursos incluídos.
