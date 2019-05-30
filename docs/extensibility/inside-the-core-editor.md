---
title: Dentro do Editor de núcleo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d400e8b122ae43424bea55c7a1d6f4bc21708707
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344336"
---
# <a name="inside-the-core-editor"></a>Dentro do editor de núcleo
O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principal é um conjunto de vários componentes que permitem que você modifique e consultar informações textuais. Se você tiver personalizado o editor principal usando a API herdada, você pode continuar a usar essas personalizações, que serão roteadas por meio de adaptadores do editor. No entanto, ele é recomendável que você adapte suas personalizações para o novo editor de API.

 As áreas a seguir estão alguns aspectos importantes do que o editor principal:

- Buffer de texto

- Exibição de texto

- Janela de código

- Marcadores de texto

- Gerenciador de texto

- Integração com serviços de linguagem

## <a name="in-this-section"></a>Nesta seção
- [Criar uma instância o editor principal usando a API herdada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) fornece instruções passo a passo sobre como usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para criar uma instância do núcleo do editor.

- [Acessar o buffer de texto, usando a API herdada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) discute a função do buffer de texto no editor de núcleo, explica os sistemas associados que são usados para acessar o buffer e fornece uma lista das interfaces implementadas pelo objeto de buffer de texto, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

- [Eventos de buffer de texto na API herdada](../extensibility/text-buffer-events-in-the-legacy-api.md) fornece uma lista das interfaces que são usados para a notificação de eventos do buffer de texto.

- [Como: Registre-se para eventos de buffer de texto com a API herdada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md) descreve como eventos de buffer de texto de aviso.

- [Use o Gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md) discute como o Gerenciador de texto é usado para compartilhar informações de preferências globais com os componentes principais do editor e como receber notificação de eventos do Gerenciador de texto.

- [Acessar o modo de exibição de theText usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) descreve a função do modo de exibição de texto no editor de núcleo e lista as interfaces implementadas pelo <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.

- [Personalizar janelas de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) fornece informações sobre como uma janela de código é usada para delimitar a exibição de texto, discute como o Gerenciador de janelas de código é usado para fornecer as decorações de janela de código e fornece notificação de novos modos de exibição .

- [Alterar configurações de exibição usando a API herdada](../extensibility/changing-view-settings-by-using-the-legacy-api.md) fornece instruções passo a passo sobre como forçar as configurações de exibição e como remover as configurações de forçado.

- [Serviços de linguagem e o editor de núcleo](../extensibility/language-services-and-the-core-editor.md) descreve a instanciação de um serviço de linguagem para as decorações de código do controle.

## <a name="related-sections"></a>Seções relacionadas
- [Passo a passo: Criar um núcleo de editor e registrar um tipo de arquivo do editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) fornece instruções passo a passo sobre como iniciar o editor principal do código gerenciado.

- [Barra de menu suspenso](../extensibility/drop-down-bar.md) discute como a barra de menu suspenso é usada na janela de código e descreve as interfaces que são usadas quando você implementa uma barra de menu suspenso.

- [Usar marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md) explica o conceito de marcadores de texto e como elas são usadas no editor de núcleo e lista as interfaces que são usadas para acessar e gerenciar marcadores de texto.

- [Como: Adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md) fornece instruções passo a passo sobre como criar um marcador de texto e como adicionar um comando personalizado a um menu de atalho.

- [Como: Criar marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md) fornece instruções passo a passo sobre como criar um marcador de texto personalizado e como fornecer o tipo de marcador, como um serviço.