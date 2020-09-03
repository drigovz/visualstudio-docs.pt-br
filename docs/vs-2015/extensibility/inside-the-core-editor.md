---
title: Dentro do editor principal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203947"
---
# <a name="inside-the-core-editor"></a>Por dentro do Editor de núcleo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal é um conjunto de vários componentes que permitem modificar e consultar informações textuais. Se você personalizou o editor principal usando a API herdada, poderá continuar a usar essas personalizações, que serão roteadas por meio de adaptadores do editor. No entanto, é recomendável que você adapte suas personalizações para a nova API do editor.  
  
 As seguintes áreas são alguns aspectos importantes do editor principal:  
  
- Buffer de texto  
  
- Exibição de texto  
  
- Janela de código  
  
- Marcadores de texto  
  
- Gerenciador de texto  
  
- Integração com serviços de linguagem  
  
## <a name="in-this-section"></a>Nesta seção  
 [Criando uma instância do editor principal usando a API herdada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Fornece instruções passo a passo sobre como usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> o para criar uma instância do editor de núcleo.  
  
 [Acessando o buffer de texto usando a API herdada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Discute a função do buffer de texto no editor principal, explica os sistemas associados que são usados para acessar o buffer e fornece uma lista das interfaces implementadas pelo objeto buffer de texto, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 [Eventos de buffer de texto na API herdada](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Fornece uma lista das interfaces que são usadas para notificação de eventos de buffer de texto.  
  
 [Como registrar para eventos de buffer de texto com a API herdada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Descreve como aconselhar eventos de buffer de texto.  
  
 [Usando o gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Discute como o Gerenciador de texto é usado para compartilhar informações de preferência global com os principais componentes do editor e como receber notificações de eventos do Gerenciador de texto.  
  
 [Acessando a exibição de texto usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Descreve a função da exibição de texto no editor principal e lista as interfaces implementadas pelo <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 [Personalizando janelas de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Fornece informações sobre como uma janela de código é usada para incluir a exibição de texto, discute como o Gerenciador de janelas de código é usado para fornecer decorações para a janela de código e fornece notificação de novas exibições.  
  
 [Alterando as configurações de exibição usando a API herdada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Apresenta instruções passo a passo sobre como forçar as configurações de exibição e como remover as configurações forçadas.  
  
 [Serviços de linguagem e o editor principal](../extensibility/language-services-and-the-core-editor.md)  
 Descreve a instanciação de um serviço de linguagem para controlar as decorações de código.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Passo a passo: Criar um editor principal e registrar um tipo de arquivo do editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Fornece instruções passo a passo sobre como iniciar o editor de núcleo do código gerenciado.  
  
 [Barra suspensa](../extensibility/drop-down-bar.md)  
 Discute como a barra suspensa é usada na janela de código e descreve as interfaces que são usadas quando você implementa uma barra suspensa.  
  
 [Usando marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Explica o conceito de marcadores de texto e como eles são usados no editor principal e lista as interfaces que são usadas para acessar e gerenciar marcadores de texto.  
  
 [Como adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)  
 Oferece instruções passo a passo sobre como criar um marcador de texto e como adicionar um comando personalizado a um menu de atalho.  
  
 [Como criar marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)  
 Oferece instruções passo a passo sobre como criar um marcador de texto personalizado e como fornecer o tipo de marcador como um serviço.
