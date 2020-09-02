---
title: Serviços de linguagem e o editor central | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180297"
---
# <a name="language-services-and-the-core-editor"></a>Serviços de linguagem e o Editor de núcleo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os editores no Visual Studio são frequentemente associados a um serviço de linguagem. Entre outras coisas, um serviço de linguagem fornece coloração de sintaxe, conclusão de instrução, IntelliSense e formatação de texto.  
  
## <a name="core-editors-and-document-data-objects"></a>Principais editores e objetos de dados de documento  
 Ao acessar o editor de núcleo, você não cria dados de documento e objetos de exibição de documento. O IDE cria e controla esses dois objetos, e você obtém identificadores para eles fazendo as chamadas apropriadas em sua implementação de fábrica do editor.  
  
 Para obter mais informações, consulte [determinando qual editor abre um arquivo em um projeto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="language-services-and-the-core-editor"></a>Serviços de linguagem e o Editor de núcleo  
 Ao implementar um serviço de linguagem, você pode controlar como os dados são exibidos no modo de exibição de documento. Um serviço de linguagem fornece informações e comportamento específicos para um determinado idioma, como Visual C++. Quando você cria um buffer de texto e determina a extensão do nome de arquivo para o documento que está abrindo, o buffer de texto determina o serviço de idioma associado a essa extensão de nome de arquivos de uma chave do registro, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Editors \\ {YOURLANGUAGESERVICE GUID} \Extensions. Em seguida, o procedimento de carregamento VSPackage padrão carrega o VSPackage e uma instância do serviço de idioma é criada.  
  
 Um serviço de linguagem básico é mostrado na ilustração a seguir.  
  
 ![Gráfico de modelo do serviço de linguagem](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Editor de núcleo e objetos de serviço de linguagem  
  
 O objeto de dados de documento para o editor principal é chamado de buffer de texto e é representado pelo <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objeto. O objeto de exibição de documento é chamado de exibição de texto e é representado pelo <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto. Esses dois objetos funcionam juntos por meio do serviço de linguagem para fornecer uma exibição unificada do editor principal. As informações do buffer de texto e da exibição de texto são exibidas em uma janela de documento chamada janela de código. O documento da janela de código é gerenciado por um Gerenciador de janelas de código.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [Fornecendo um contexto de serviço de linguagem usando a API herdada](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [Hospedagem do IntelliSense](../extensibility/intellisense-hosting.md)   
 [Idiomas contidos](../extensibility/contained-languages.md)   
 [Desenvolvendo um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)
