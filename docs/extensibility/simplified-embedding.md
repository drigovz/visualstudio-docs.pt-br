---
title: Incorporação Simplificada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700080"
---
# <a name="simplified-embedding"></a>Incorporação simplificada
A incorporação simplificada é habilitada em um editor quando seu objeto de exibição [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> documento é criado (ou seja, feito filho) , e a interface é implementada para lidar com seus comandos de janela. Editores de incorporação simplificadas não podem hospedar controles ativos. Os objetos usados para criar um editor com incorporação simplificada são mostrados na ilustração a seguir.

 ![Gráfico do Editor de Incorporação Simplificada](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplificadEmincorporaçãoEditor") Editor com incorporação simplificada

> [!NOTE]
> Dos objetos nesta ilustração, apenas o `CYourEditorFactory` objeto é necessário para criar um editor baseado em arquivos padrão. Se você está criando um editor personalizado, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>você não é obrigado a implementar, porque seu editor provavelmente terá seu próprio mecanismo de persistência privado. Para editores não personalizados, no entanto, você deve fazê-lo.

 Todas as interfaces implementadas para criar um editor `CYourEditorDocument` com incorporação simplificada estão contidas no objeto. No entanto, para suportar várias visualizações de dados de documentos, divida as interfaces em dados separados e visualize objetos conforme indicado na tabela a seguir.

|Interface|Localização da interface|Use|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Exibir|Fornece conexão à janela pai.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Exibir|Manuseia comandos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Exibir|Habilita atualizações da barra de status.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Exibir|Habilita itens **da caixa de ferramentas.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dados|Envia notificações quando o arquivo é alterado.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dados|Habilita o recurso Salvar as para um tipo de arquivo.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dados|Permite a persistência do documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dados|Permite a supressão de eventos de alteração de arquivo, como o acionamento de recarga.|
