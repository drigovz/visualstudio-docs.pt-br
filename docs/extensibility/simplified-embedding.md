---
title: Incorporação simplificada | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700080"
---
# <a name="simplified-embedding"></a>Incorporação simplificada
A incorporação simplificada é habilitada em um editor quando seu objeto de exibição de documento é pai de (ou seja, tornou-se um filho de) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface é implementada para manipular seus comandos de janela. Editores de inserção simplificados não podem hospedar controles ativos. Os objetos usados para criar um editor com inserção simplificada são mostrados na ilustração a seguir.

 ![Gráfico do editor de inserção simplificado](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor com incorporação simplificada

> [!NOTE]
> Dos objetos nesta ilustração, somente o `CYourEditorFactory` objeto é necessário para criar um editor padrão baseado em arquivo. Se você estiver criando um editor personalizado, não precisará implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , porque seu editor provavelmente terá seu próprio mecanismo de persistência privada. No entanto, para editores não personalizados, você deve fazer isso.

 Todas as interfaces implementadas para criar um editor com incorporação simplificada estão contidas no `CYourEditorDocument` objeto. No entanto, para dar suporte a várias exibições de dados de documento, divida as interfaces em dados separados e exiba objetos conforme indicado na tabela a seguir.

|Interface|Local da interface|Uso|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Visualizar|Fornece conexão com a janela pai.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Visualizar|Manipula comandos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizar|Habilita atualizações da barra de status.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizar|Habilita itens da **caixa de ferramentas** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dados|Envia notificações quando o arquivo é alterado.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dados|Habilita o recurso salvar como para um tipo de arquivo.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dados|Habilita a persistência para o documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dados|Permite a supressão de eventos de alteração de arquivo, como o disparo de recarregamento.|
