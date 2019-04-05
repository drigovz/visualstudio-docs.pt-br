---
title: Detalhes de tempo de execução do controle de origem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb52770557fa37a14040b686dcdfbf345a713a2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926994"
---
# <a name="source-control-runtime-details"></a>Detalhes de tempo de execução de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um projeto é adicionado ao controle de origem quando o usuário adiciona um arquivo no projeto ao controle de origem, ou por meio de um controlador de automação, como um assistente. Um projeto não especifica para si mesmo que está sob controle do código-fonte; Ele dá suporte ao controle do código-fonte, mas deve ser adicionado manualmente a ele.  
  
## <a name="registering-with-a-source-control-package"></a>Registrando com um pacote de controle do código-fonte  
 Quando um arquivo em seu projeto é adicionado ao controle de origem, o ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> para fornecer a você quatro cadeias de caracteres opacas que são usadas como cookies pelo sistema de controle de origem. Store essas cadeias de caracteres no arquivo de projeto. Essas cadeias de caracteres devem ser passadas para o Stub de controle do código-fonte (o componente do Visual Studio que gerencia os pacotes de controle do código-fonte) durante a inicialização do tipo de projeto chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Isso por sua vez carrega o pacote de controle de origem apropriado e encaminha a chamada para sua implementação de `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Oferecer suporte ao controle do código-fonte](../../extensibility/internals/supporting-source-control.md)
