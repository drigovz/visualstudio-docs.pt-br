---
title: Determinando se uma VSPackage de controle do código-fonte deve ser implementada | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196796"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Determinando se deseja implementar um VSPackage de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta seção elabora as opções de plug-ins de controle do código-fonte e VSPackages de controle do código-fonte para estender soluções de controle do código-fonte e fornece diretrizes abrangentes sobre como escolher um caminho de integração adequado.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Pequena solução de controle do código-fonte com recursos limitados  
 Se você tiver recursos limitados e não puder ser carregado com a sobrecarga de escrever um pacote de controle do código-fonte, você poderá criar plug-ins baseados em API de plug-in de controle do código-fonte. Isso permite que você trabalhe lado a lado com pacotes de controle do código-fonte, e você pode alternar entre plug-ins de controle do código-fonte e pacotes sob demanda. Para obter mais informações, consulte [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solução de controle do código-fonte grande com um rico conjunto de recursos  
 Se você quiser implementar uma solução de controle do código-fonte que fornece um modelo de controle do código-fonte avançado que não é capturado adequadamente usando a API de plug-in de controle do código-fonte, você pode considerar um pacote de controle do código-fonte como o caminho de integração. Isso se aplica especialmente se você preferir substituir o pacote do adaptador de controle do código-fonte (que se comunica com plug-ins de controle do código-fonte e fornece uma interface do usuário de controle do código-fonte básica) com o seu próprio para que você possa manipular os eventos de controle do código-fonte de maneira personalizada. Se você já tiver uma interface do usuário de controle do código-fonte satisfatória e quiser preservar essa experiência no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , a opção do pacote de controle do código-fonte permitirá que você faça exatamente isso. O pacote de controle do código-fonte não é genérico e é projetado exclusivamente para uso com o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 Se você quiser implementar uma solução de controle do código-fonte que forneça flexibilidade e controle mais avançado sobre a lógica de controle do código-fonte e a interface do usuário, você pode preferir a rota de integração do pacote de controle do código-fonte Você pode:  
  
1. Registre seu próprio VSPackage de controle do código-fonte (consulte [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2. Substitua a interface do usuário do controle do código-fonte por sua interface do usuário personalizada (consulte a [interface de usuários personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3. Especifique os glifos a serem usados e manipule Gerenciador de Soluções eventos de glifo (consulte [controle de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4. Manipule eventos de edição de consulta e salvar consulta (veja [consulta editar consulta salvar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Consulte Também  
 [Criando um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)
