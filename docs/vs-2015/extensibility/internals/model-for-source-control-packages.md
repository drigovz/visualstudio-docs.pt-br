---
title: Modelo para pacotes de controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 811cdfa2cbae85d6509e7cd883c5675b81639fa0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928570"
---
# <a name="model-for-source-control-packages"></a>Modelo de pacotes de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O modelo a seguir representa um exemplo de uma implementação de controle do código-fonte. No modelo, você pode ver as que você deve implementar interfaces e os serviços de ambiente que você deve chamar. Assim como todos os serviços, você realmente chama os métodos de uma interface específica que você obtém por meio do serviço. Os nomes das classes são identificados para torná-lo mais fácil de ver como o controle de origem é realizado.  
  
 ![SCC&#95;exemplos de SCRIP](../../extensibility/internals/media/scc-tup.gif "SCC_TUP")  
Projeto de controle de fonte de exemplo  
  
## <a name="interfaces"></a>Interfaces  
 Você pode implementar o controle do código-fonte para seus novos tipos de projeto no Visual Studio usando a lista de interfaces mostrado na tabela a seguir.  
  
|Interface|Use|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chamado por projetos e editores antes de eles salvar ou arquivos de alteração (sujo). Essa interface é acessada usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chamado por projetos para solicitar permissão para adicionar, remover ou renomear um arquivo ou diretório. Essa interface também é chamada por projetos para informar o ambiente quando uma adição aprovada, remova ou renomeie a ação for concluído. Ele é acessado usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementada por qualquer entidade que registra para ser notificado quando os projetos de adicionar, renomeiam ou remover um arquivo ou diretório. Para se registrar para notificação de eventos, chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Chamado por projetos para registrar com o pacote de controle do código-fonte e obter informações sobre o status de controle do código-fonte. Essa interface é acessada usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementado pelo projeto para responder a solicitações de controle do código-fonte para obter informações sobre arquivos e obter a fonte de configurações de controle necessárias para o arquivo de projeto.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Oferecer suporte ao controle do código-fonte](../../extensibility/internals/supporting-source-control.md)
