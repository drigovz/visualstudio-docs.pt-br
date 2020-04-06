---
title: Determinando se implementar á fonte de controle de origem VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708717"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Determine se deve implementar um VSPackage de controle de origem
Esta seção elabora as opções de plug-ins de controle de fonte e controle de origem VSPackages para ampliar soluções de controle de origem e fornece diretrizes amplas sobre a escolha de um caminho de integração adequado.

## <a name="small-source-control-solution-with-limited-resources"></a>Solução de controle de pequena fonte com recursos limitados
 Se você tiver recursos limitados e não puder ser sobrecarregado com a sobrecarga de escrever um pacote de controle de origem, você pode criar plug-ins baseados em API de controle de fonte. Para obter mais informações, consulte [Inscrição e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Grande solução de controle de origem com um rico conjunto de recursos
 Se você quiser implementar uma solução de controle de origem que forneça um modelo rico de controle de origem que não seja capturado adequadamente usando a API plug-in de controle de origem, você pode considerar um pacote de controle de origem como o caminho de integração. Isso se aplica especialmente se você preferir substituir o Pacote adaptador de controle de origem (que se comunica com plug-ins de controle de origem e fornece uma interface de usuário de controle de origem básica) com a sua própria para que você possa lidar com os eventos de controle de origem de forma personalizada. Se você já tem uma ui de controle de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fonte satisfatória e quer preservar essa experiência em , a opção de pacote de controle de origem permite que você faça exatamente isso. O pacote de controle de origem não é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] genérico e foi projetado exclusivamente para uso com IDE.

 Se você quiser implementar uma solução de controle de origem que forneça flexibilidade e controle mais rico sobre a lógica de controle de origem e a iu, você pode preferir a rota de integração do pacote de controle de origem. Você pode:

1. Registre seu próprio controle de origem VSPackage (ver [Registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Substitua a interface de usuário padrão do controle de origem por sua interface de usuário personalizada (veja [interface de usuário personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. Especifique glifos a serem usados e manuseie eventos de glifos do Solution Explorer (veja [controle de glifos](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. Lidar com eventos Editar e salvar consulta (consulte [Consultar editar consulta salvar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>Confira também
- [Criar um plug-in de controle de origem](../../extensibility/internals/creating-a-source-control-plug-in.md)
