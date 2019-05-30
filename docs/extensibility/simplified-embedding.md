---
title: Incorporação simplificada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c77c7f19ff677ddbe8339c88ef3ea46953e23b7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332068"
---
# <a name="simplified-embedding"></a>Incorporação simplificada
Incorporação simplificada é habilitado em um editor, quando seu objeto de exibição de documento tiver um pai (ou seja, feitas de um filho) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface é implementada para lidar com seus comandos de janela. Editores de incorporação simplificadas não é possível hospedar controles Active Directory. Os objetos usados para criar um editor com a incorporação simplificada são mostrados na ilustração a seguir.

 ![Gráfico de Editor de incorporação simplificado](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor com a incorporação simplificada

> [!NOTE]
> Os objetos nesta ilustração, somente o `CYourEditorFactory` objeto é necessária para criar um editor padrão baseado em arquivo. Se você estiver criando um editor personalizado, não é necessário implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, porque seu editor provavelmente terá seu próprio mecanismo de persistência privada. Para editores não personalizado, no entanto, você deve fazer isso.

 Todas as interfaces implementadas para criar um editor com a incorporação simplificada estão contidas no `CYourEditorDocument` objeto. No entanto, para dar suporte a vários modos de exibição de dados de documentos, divida as interfaces em objetos separados de dados e exibição conforme indicado na tabela a seguir.

|Interface|Localização da interface|Use|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Exibir|Fornece a conexão para a janela pai.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Exibir|Lida com comandos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Exibir|Permite atualizações da barra de status.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Exibir|Habilita **caixa de ferramentas** itens.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dados|Envia notificações quando o arquivo é alterado.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dados|Habilita o recurso Salvar como para um tipo de arquivo.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dados|Habilita a persistência para o documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dados|Permite a supressão de eventos de alteração de arquivo, como recarregar disparando.|