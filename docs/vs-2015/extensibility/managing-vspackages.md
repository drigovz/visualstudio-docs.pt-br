---
title: Gerenciando VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194381"
---
# <a name="managing-vspackages"></a>Gerenciando VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na maioria dos casos, você não precisa se preocupar com o gerenciamento de VSPackages, já que os modelos de projeto e item registram e carregam o pacote automaticamente. No entanto, em algumas circunstâncias, talvez seja necessário aprender um pouco mais para gerenciar seu pacote.  
  
## <a name="using-the-experimental-instance"></a>Usando a instância experimental  
 Para saber mais sobre a instância experimental, consulte [a instância experimental](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrando e cancelando o registro de VSPackages  
 Para saber como registrar e cancelar o registro de VSPackages e outros tipos de extensão, consulte [registrando e cancelando o registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Carregando um VSPackage  
 VSPackages pode ser definido como AutoLoad quando um GUID de CMDUICONTEXT específico é ativado. Para obter mais informações, consulte [carregando VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Usando AsyncPackage para carregar VSPackages em segundo plano  
 A classe AsyncPackage permite o carregamento de pacotes em um thread em segundo plano para melhorar a capacidade de resposta da interface do usuário no Visual Studio. Para obter mais informações, consulte [como: usar AsyncPackage para carregar VSPackages em segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interface do usuário baseado em regra para extensões  
 Os contextos de interface do usuário baseados em regras permitem que os autores de extensão definam as condições exatas sob as quais um contexto de interface do usuário é ativado e VSPackages associado são carregados. Para obter mais informações, consulte [como usar o contexto de interface do usuário com base em regras para extensões do Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Solucionando problemas de VSPackages  
 Descubra as técnicas para solucionar problemas de VSPackages que não carregam ou estão ocorrendo erros: [solução de problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Consulte Também  
 [VSPackages](../extensibility/internals/vspackages.md)
