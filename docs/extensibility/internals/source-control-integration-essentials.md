---
title: Essenciais de Integração de Controle de Fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705234"
---
# <a name="source-control-integration-essentials"></a>Conceitos básicos da integração do controle do código-fonte
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]suporta dois tipos de integração de controle de origem: um plug-in de controle de origem que fornece funcionalidade básica e é construído usando a API plug-in de controle de fonte (anteriormente conhecida como API MSSCCI) e uma solução de integração de controle de origem baseada em VSPackage que fornece funcionalidade mais robusta.

## <a name="source-control-plug-in"></a>Plug-in de controle de origem
 Um Plug-in de controle de origem é escrito como um DLL que implementa a API plug-in de controle de origem. A funcionalidade de integração de registro e controle de origem é fornecida através da API. Essa abordagem é mais fácil de implementar do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que um VSPackage de controle de origem, e usa a interface do usuário (UI) para a maioria das operações de controle de origem.

 Para implementar um plug-in de controle de origem usando a API plug-in de controle de origem, siga estas etapas:

1. Crie uma DLL que implemente as funções especificadas nos [Plug-ins de controle de fonte](../../extensibility/source-control-plug-ins.md).

2. Registre o DLL fazendo as entradas de registro apropriadas, conforme descrito em [Como: Instalar um Plug-in de Controle de Origem](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).

3. Crie uma iu de ajuda e exiba-a quando solicitada [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pelo Pacote adaptador de controle de fonte (o componente que lida com a funcionalidade de controle de origem através de plug-ins de controle de origem).

   Para obter mais informações, consulte [Criando um Plug-in de Controle de Origem](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Controle de origem VSPackage
 Um controle de origem A implementação do VSPackage permite que você desenvolva uma substituição personalizada para a ui de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controle de origem. Essa abordagem fornece controle completo sobre a integração do controle de origem, mas exige que você forneça os elementos de interface de interface e implemente as interfaces de controle de origem que de outra forma seriam fornecidas sob a abordagem plug-in.

 Para implementar um VSPackage de controle de origem, você deve:

1. Crie e registre seu próprio controle de origem VSPackage, conforme descrito em [Registro e Seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Substitua a interface do rei do controle de origem padrão por sua interface do tempo personalizada. Consulte [interface de usuário personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Especifique glifos a serem usados e manuseie eventos de glifos **do Solution Explorer.** Consulte [o Controle de Glifos.](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Lidar com eventos Editar e salvar consulta, como mostrado no [ConsultaRy Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Para obter mais informações, consulte [Criando um VsPackage de Controle de Origem](../../extensibility/internals/creating-a-source-control-vspackage.md).

## <a name="see-also"></a>Confira também
- [Visão geral](../../extensibility/internals/source-control-integration-overview.md)
- [Criando um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)
