---
title: Visão geral da criação de perfil de script ativo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ce6f7fe29fca2cd17c3dfcce76dac40e422aba4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572722"
---
# <a name="active-script-profiling-overview"></a>Visão geral da criação de perfil de script ativo
As [interfaces do criador de perfil de script ativo](../winscript/reference/active-script-profiler-interfaces.md) permitem a criação de perfil de um mecanismo de script. A criação de perfil do script ativo consiste das seguintes partes:  
  
- Mecanismo de linguagem  
  
- Host  
  
- Criador de Perfil  
  
## <a name="language-engine"></a>Mecanismo de linguagem  
 O mecanismo de linguagem executa o script. Ele fornece métodos que permitem a criação de perfil do código do script conforme ele é executado. Quando a criação de perfil é habilitada, o mecanismo de linguagem usa o CLSID (identificador de classe) do objeto COM do criador de perfil como um argumento. Ele cria uma instância do objeto COM do criador de perfil e chama o criador de perfil quando eventos diversos ocorrem.  
  
 O mecanismo de linguagem implementa a [Interface IActiveScriptProfilerControl](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
> O tempo de execução da linguagem [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] verifica a variável de ambiente JS_PROFILER na criação para determinar se a criação de perfil deve ser habilitada. Se essa variável é definida para o CLSID do criador de perfil, o runtime da linguagem cria uma instância do objeto COM do criador de perfil, usando o valor da variável para determinar qual criador de perfil criar.  
  
## <a name="host"></a>Host  
 O host cria o mecanismo de linguagem e fornece a ele scripts a serem executados. Um host inteligente também fornece o contexto de documento que pode ser usado por um depurador ou criador de perfil para fornecer melhores informações quando você está depurando ou criando perfis.  
  
## <a name="profiler"></a>Criador de Perfil  
 O criador de perfil recebe as chamadas do mecanismo de linguagem quando eventos diversos ocorrem. O criador de perfil deve ser registrado como um objeto COM e deve implementar a [Interface IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../winscript/reference/active-script-profiler-interfaces.md)