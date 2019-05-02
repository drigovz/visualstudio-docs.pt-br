---
title: Determinar se deve implementar um VSPackage de controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cff53700dcd6a80f841108d5a2b486dcb0ba7a11
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090836"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Determinando se deseja implementar um VSPackage de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta seção aborda as opções de plug-ins de controle do código-fonte e os VSPackages de controle de origem para estender o controle de fonte de soluções e fornece diretrizes amplas sobre como escolher um caminho de integração adequada.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Solução de controle de origem pequenas com recursos limitados  
 Se você tiver recursos limitados e não pode ser sobrecarregado com a sobrecarga de escrever um pacote de controle do código-fonte, você pode criar plug-ins baseados na API de plug-in de controle do código-fonte. Isso permite que você trabalhe lado a lado com pacotes de controle do código-fonte, e você pode alternar entre pacotes sob demanda e plug-ins de controle de origem. Para obter mais informações, consulte [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solução de controle de origem grande com um conjunto rico de recursos  
 Se você quiser implementar uma solução de controle do código-fonte que fornece um modelo de controle de fonte avançada que não é capturado adequadamente, usando a API de plug-in de controle do código-fonte, você pode considerar um pacote de controle do código-fonte como o caminho de integração. Isso se aplica especialmente se você substituiria o pacote do adaptador de controle de origem (que se comunica com o plug-ins de controle do código-fonte e fornece um controle de origem básico da interface do usuário) em vez disso, com seu próprio para que você pode manipular os eventos de controle de origem de uma maneira personalizada. Se você já tiver uma fonte satisfatória de controle da interface do usuário e deseja preservar essa experiência em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], a opção de controle de origem do pacote lhe permite fazer exatamente isso. O pacote de controle de origem não é genérico e destina-se unicamente para uso com [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 Se você quiser implementar uma solução de controle do código-fonte que fornece flexibilidade e controle avançado sobre a lógica de controle do código-fonte e a interface do usuário, talvez você prefira a rota de integração de pacote de controle de origem. Você pode:  
  
1. Registrar seu próprio VSPackage de controle do código-fonte (consulte [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2. Substitua o controle de fonte padrão da interface do usuário com sua interface do usuário personalizada (consulte [Interface de usuário personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3. Especifique os glifos a ser usada e manipular eventos de glifo do Gerenciador de soluções (veja [controle de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4. Manipular eventos de consulta de editar e salvar consulta (consulte [consulta Editar consulta salvar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Consulte também  
 [Criar um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)
