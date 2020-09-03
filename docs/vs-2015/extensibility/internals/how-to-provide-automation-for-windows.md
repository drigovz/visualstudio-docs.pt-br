---
title: 'Como: fornecer automação para o Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea7b79df4e7f3748ec2bc7f5e57c6ecb7dfca5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191839"
---
# <a name="how-to-provide-automation-for-windows"></a>Como fornecer automação para o Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Você pode fornecer automação para janelas de documentos e ferramentas. Fornecer automação é aconselhável sempre que você deseja disponibilizar objetos de automação em uma janela, e o ambiente ainda não fornece um objeto de automação pronto, como faz com uma lista de tarefas.  
  
## <a name="automation-for-tool-windows"></a>Automação para janelas de ferramentas  
 O ambiente fornece automação em uma janela de ferramenta retornando um <xref:EnvDTE.Window> objeto padrão, conforme explicado no procedimento a seguir:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Para fornecer automação para janelas de ferramentas  
  
1. Chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método por meio do ambiente com o <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> `VSFPROPID` parâmetro as para obter o `Window` objeto.  
  
2. Quando um chamador solicita um objeto de automação específico do VSPackage para a janela de ferramentas por meio do <xref:EnvDTE.Window.Object%2A> , o ambiente chama `QueryInterface` para `IExtensibleObject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> ou as `IDispatch` interfaces. `IExtensibleObject`E `IVsExtensibleObject` fornecem um <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> método.  
  
3. Quando o ambiente chama o `GetAutomationObject` método passando `NULL` , responde passando o objeto específico do VSPackage.  
  
4. Se `QueryInterface` a chamada for `IExtensibleObject` e `IVsExtensibleObject` falhar, o ambiente chamará `QueryInterface` para `IDispatch` .  
  
## <a name="automation-for-document-windows"></a>Automação para janelas de documentos  
 Um <xref:EnvDTE.Document> objeto padrão também está disponível no ambiente, embora um editor possa ter sua própria implementação do `T:EnvDTE.Document` objeto implementando a `IExtensibleObject` interface e respondendo ao `GetAutomationObject` .  
  
 Além disso, um editor pode fornecer um objeto de automação específico do VSPackage, recuperado por meio do <xref:EnvDTE.Document.Object%2A> método, implementando as `IVsExtensibleObject` `IExtensibleObject` interfaces ou. Os [exemplos de VSSDK](../../misc/vssdk-samples.md) contribuem com um objeto de automação de RTF específico do documento.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
