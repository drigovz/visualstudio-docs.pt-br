---
title: Modelo de um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707042"
---
# <a name="model-of-a-legacy-language-service"></a>Modelo de um serviço de linguagem herdado
Um serviço de idioma define os elementos e recursos para um idioma específico, e é usado para fornecer ao editor informações específicas para esse idioma. Por exemplo, o editor precisa conhecer os elementos e palavras-chave do idioma para suportar a coloração da sintaxe.

 O serviço de idiomas funciona em estreita colaboração com o buffer de texto gerenciado pelo editor e a exibição que contém o editor. A opção Microsoft IntelliSense **Quick Info** é um exemplo de um recurso fornecido por um serviço de idiomas.

## <a name="a-minimal-language-service"></a>Um serviço mínimo de idioma
 O serviço de idioma mais básico contém os seguintes dois objetos:

- O serviço de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> *idiomas* implementa a interface. Um serviço de idioma saem com informações sobre o idioma, incluindo nome, extensões de nome de arquivo, gerenciador de janelas de código e colorador.

- O *colorador* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> implementa a interface.

  O desenho conceitual a seguir mostra um modelo de um serviço de linguagem básica.

  ![Gráfico do modelo de serviço de idioma](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Modelo básico de serviço de linguagem

  A janela do documento hospeda a *exibição* do documento do editor, neste caso o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor principal. A exibição do documento e o buffer de texto são de propriedade do editor. Esses objetos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funcionam através de uma janela de documento especializada chamada *janela de código*. A janela de código <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> está contida em um objeto que é criado e controlado pelo IDE.

  Quando um arquivo com uma determinada extensão é carregado, o editor localiza o serviço de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> idioma associado a essa extensão e passa para ele a janela de código chamando o método. O serviço de idiomaretorna um *gerenciador de janelas de*código , que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface.

  A tabela a seguir fornece uma visão geral dos objetos no modelo.

| Componente | Objeto | Função |
|------------------| - | - |
| Buffer de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Um fluxo de texto de leitura/gravação unicode. É possível que o texto use outras codificações. |
| Janela de código | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Uma janela de documento que contenha uma ou mais visualizações de texto. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está no modo De interface de vários documentos (MDI), a janela de código é uma criança MDI. |
| Exibição de texto | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Uma janela que permite ao usuário navegar e visualizar texto usando o teclado e o mouse. Uma exibição de texto aparece para o usuário como um editor. Você pode usar visualizações de texto em janelas de editor ordinários, na janela Saída e na janela 'Imediato'. Além disso, você pode configurar uma ou mais exibições de texto dentro de uma janela de código. |
| Gerenciador de texto | Gerenciado pelo <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> serviço, a partir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> do qual você obtém um ponteiro | Um componente que mantém informações comuns compartilhadas por todos os componentes descritos anteriormente. |
| Serviço de idiomas | Dependente da implementação; Implementa<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Um objeto que fornece ao editor informações específicas do idioma, como destaque de sintaxe, conclusão da instrução e correspondência de suporte. |

## <a name="see-also"></a>Confira também
- [Dados de documentos e exibição de documentos em editores personalizados](../../extensibility/document-data-and-document-view-in-custom-editors.md)
