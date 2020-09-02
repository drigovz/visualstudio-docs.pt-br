---
title: Atributos de suporte do site | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144305"
---
# <a name="web-site-support-attributes"></a>Atributos de suporte a site
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] O projeto de site pode ser estendido para fornecer suporte a linguagens de programação da Web. O idioma deve se registrar com [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para que os modelos de projeto possam aparecer na caixa de diálogo **novo site** quando o idioma for selecionado.  
  
 O exemplo do IronPython Studio inclui suporte a sites da Web. Você pode encontrá-lo com os [exemplos de VSSDK](../../misc/vssdk-samples.md). Ele inclui as seguintes classes de atributo para registrar o IronPython como uma linguagem codebehind para novos projetos Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Esse atributo é colocado no projeto de idioma. Ele adiciona o idioma à lista de linguagens de programação da Web na lista **idioma** da caixa de diálogo **novo site da Web** . Por exemplo, o seguinte adiciona IronPython à lista:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Esse atributo também define o caminho de modelos para apontar para a pasta modelos. Para obter mais informações sobre o local da pasta modelos, consulte [modelos de suporte do site](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Esse atributo é colocado no projeto de idioma. Ele permite que o projeto de site aninhe um tipo de arquivo (relacionado) em outro tipo de arquivo (primário) no **Gerenciador de soluções**.  
  
 Por exemplo:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Especifica que um arquivo codebehind do IronPython está relacionado a um arquivo. aspx. Quando uma nova página da Web. aspx é criada em uma solução de site da IronPython, um novo arquivo de origem. py é gerado e exibido como um nó filho da página. aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Esse atributo é colocado no pacote de projeto de idioma. Ele seleciona o provedor IntelliSense para o idioma.  
  
 Por exemplo:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Especifica que uma instância de PythonIntellisenseProvider, que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , deve ser criada sob demanda para fornecer serviços de linguagem.  
  
 A implementação de IVsIntellisenseProject manipula referências e chama o compilador de linguagem quando uma página da Web com código é solicitada, mas não é armazenada em cache.  
  
## <a name="see-also"></a>Consulte Também  
 [Suporte a site](../../extensibility/internals/web-site-support.md)
