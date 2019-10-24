---
title: Modelo para pacotes de controle do código-fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a9ae5f2704d625da2212e92626c33fb384ebbc5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726562"
---
# <a name="model-for-source-control-packages"></a>Modelo de pacotes de controle do código-fonte
O modelo a seguir representa um exemplo de uma implementação de controle do código-fonte. No modelo, você vê as interfaces que você deve implementar e os serviços de ambiente que você deve chamar. Como todos os serviços, você realmente chama os métodos de uma interface específica que você obtém por meio do serviço. Os nomes das classes são identificados para facilitar a visualização de como o controle do código-fonte é executado.

 ![Exemplos&#95;de SCC scrip](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Exemplo de projeto de controle do código-fonte

## <a name="interfaces"></a>Interfaces
 Você pode implementar o controle do código-fonte para seus novos tipos de projeto no Visual Studio usando a lista de interfaces mostrada na tabela a seguir.

|Interface|Use|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chamado por projetos e editores antes que eles salvem ou alterem arquivos (sujos). Essa interface é acessada usando o serviço de <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chamado por projetos para solicitar permissão para adicionar, remover ou renomear um arquivo ou diretório. Essa interface também é chamada por projetos para informar o ambiente quando uma ação de adição, remoção ou renomeação aprovada for concluída. Ele é acessado usando o serviço de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementado por qualquer entidade que se registra para ser notificado quando os projetos adicionam, renomeam ou removem um arquivo ou diretório. Para se registrar para notificação de eventos, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Chamado por projetos para registrar com o pacote de controle do código-fonte e obter informações sobre o status do controle do código-fonte. Essa interface é acessada usando o serviço de <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementado pelo projeto para responder às solicitações de controle do código-fonte de informações sobre arquivos e obter as configurações de controle do código-fonte necessárias para o arquivo de projeto.|

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Oferecer suporte ao controle do código-fonte](../../extensibility/internals/supporting-source-control.md)