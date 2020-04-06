---
title: Modelo para Pacotes de Controle de Origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707064"
---
# <a name="model-for-source-control-packages"></a>Modelo de pacotes de controle do código-fonte
O modelo a seguir representa um exemplo de implementação de controle de origem. No modelo, você vê as interfaces que você deve implementar e os serviços ambientais que você deve chamar. Como todos os serviços, você realmente chama os métodos de uma interface específica que você obtém por meio do serviço. Os nomes das classes são identificados para facilitar a veja como o controle de origem é realizado.

 ![SCC&#95;Exemplos de TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Projeto de Controle de Origem de Exemplo

## <a name="interfaces"></a>Interfaces
 Você pode implementar o controle de origem para seus novos tipos de projeto no Visual Studio usando a lista de interfaces mostradas na tabela a seguir.

|Interface|Use|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chamado por projetos e editores antes de salvar ou alterar arquivos (sujos). Esta interface é acessada usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> serviço.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chamado por projetos para solicitar permissão para adicionar, remover ou renomear um arquivo ou diretório. Essa interface também é chamada por projetos para informar o ambiente quando uma ação de adição, remoção ou renomeação aprovada estiver concluída. Ele é acessado <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> usando o serviço.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementado por qualquer entidade que se registre para ser notificada quando os projetos adicionarem, renomearem ou removerem um arquivo ou diretório. Para se inscrever para <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>notificação de eventos, ligue .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Chamado por projetos para se registrar com o pacote de controle de origem e para obter informações sobre o status de controle de origem. Esta interface é acessada usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> serviço.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementado pelo projeto para responder às solicitações de controle de origem para obter informações sobre arquivos e para obter as configurações de controle de origem necessárias para o arquivo do projeto.|

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Suporte para controle do código-fonte](../../extensibility/internals/supporting-source-control.md)
